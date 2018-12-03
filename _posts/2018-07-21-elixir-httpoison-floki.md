---
layout: post
title:  "Elixir Httpoison Floki scrapper"
date:   2018-07-21 22:25:05
author: Mahabub Islam
categories: technology elixir scrapper httpoison
image: true
---

Github Link of the repo: https://github.com/prio101/gurdian_scrapper
I started to work with elixir language short time ago. And as people say, there are no other way better than creating small one or two side projects to sharpen your skill sets.

So, I started to think of creating a small scrapper script with elixir language specifically for this resource page on TheGurdian . They tried to crowd source and collect quotes and book data accordingly with time.

    As example,

    00:00:00h - “He is certain he heard footsteps: they come nearer, and then die away. The ray of light beneath his door is extinguished. It is midnight; someone has turned out the gas; the last servant has gone to bed, and he must lie all night in agony with no one to bring him any help.”

    Swann’s Way Marcel Proust - @westrowc

So, at the very first I created a mix project for elixir language. With command,

    > mix new gurdian_scrapper

This created a ready to work with mix project on the path. After that I put Httpoison and Floki over mix.exs and ran

    > mix deps.get

And this command fetched the packages over local directory for the usage.

From here mostly what I have done is, Using httpoison to call and get the response from the url of TheGurdian page and later with Floki parse the data and saved it over a new text file.

In specific three steps it would be like, Fetching the response,

    def start_and_fetch_response do
    IO.puts "starting"
    HTTPoison.start
    url = 'https://www.theguardian.com/books/table/2011/apr/21/literary-clock'
    case HTTPoison.get(url) do
      {:ok, %HTTPoison.Response{status_code: 200, body: body}} ->
        file = File.open!("data_save_scrapped.txt", [:write, :utf8])
        parse_by_id(body, 0, file)
      {:ok, %HTTPoison.Response{status_code: 404}} ->
        IO.puts "Not found :("
      {:error, %HTTPoison.Error{reason: reason}} ->
        IO.inspect reason
    end
    end

Formatting the response with Floki,

    def parse_by_id(body, n, file) when n <= 934 do

        by_td_data(body, n, file)

        parse_by_id(body, n + 1, file)

    end

    def parse_by_id(_body, _n, file) do

        File.close file

    end

    def by_td_data(body, i, file) do

    Enum.each(0..4, fn j ->

    body

    |> Floki.find("#table-cell-7619-#{i}-#{j}")

    |> Floki.text

    |> (fn x -> save_into_txt_file(x, file) end).()

    end)

    end

And after that I just saved it over the file,    


    def save_into_txt_file(data, file) do

        IO.binwrite(file, data <>", \n" )

    end

After this I just ran,    

    > iex -S mix
    ->> GurdianScrapper.start_and_fetch_response

And this saves the scrapped data onto the file on the same project directory .

So, that’s all for today, its fun to work with elixir language. Maybe next time I will be able to share something more with you people.
    
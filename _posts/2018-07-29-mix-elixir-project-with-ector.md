---
layout: post
title:  "Mix Elixir project with Ecto"
date:   2018-07-29 22:25:05
author: Mahabub Islam
categories: technology elixir ecto mix
image: true
---

In this post I am going to share how to make a Mix project with Elixir and Ecto. I was using Elixir 1.7.3 while making this project.
For this section, I started with an empty template of the mix project but its a template. More about this can be found over here.

After installing it I pulled a template form hex,

    mix template.install hex gen_template_ecto_service

and after this run command to have a mix project with Ecto,    

    mix gen ecto_service project_name --module_name=ModuleName
    cd project_name
    mix deps.get

Now I have to open the project and update the credentials over the <code>config/dev.exs</code>    

    use Mix.Config

    config :todolist, TodoList.Repo, [
        adapter: Ecto.Adapters.Postgres,
        database: "todolist_#{Mix.env}",
        username: "postgres",
        password: "",
        hostname: "localhost",
    ]

after we can run the command over terminal,

    mix ecto.create     

It will create a database with the project name. And will initialize the Repo.

After this, I tried to create Migration and generate it.

    mix ecto.gen.migration create_tasks_table 

And write the migration, into '/repo/migration/migration_file_name'    

        defmodule TodoList.Repo.Migrations.CreateTasks do
        use Ecto.Migration

            def change do
                create table("tasks") do
                add :task_name, :string
                add :task_description, :string
                add :task_status, :string
                timestamps()
                end
            end
        end

And run, `mix ecto.migrate  `

After this to spin up a CRUD app to check the power of the Ecto I created,

`todo_list/task.ex` over the Module directory.

        defmodule TodoList.Task do
            use Ecto.Schema
            import Poison 
            alias TodoList.Repo

            schema "tasks" do
                field :task_name
                field :task_description
                field :task_status

            timestamps()
        end

            def tasks do
                Repo.all TodoList.Task
            end

            def create_task(name, description, status) do
                %TodoList.Task{task_name: name, task_description: description, task_status: status}
                |> Repo.insert()
            end

            def show_task(id) do
                Repo.get!(TodoList.Task, id)
                |> convert_to_map
                |> drop_meta
                |> encode_poison
            end

            def update_task(id, changeset) do
                task = Repo.get!(TodoList.Task, id)
                task_change = Ecto.Changeset.change task, changeset

                case Repo.update task_change do
                {:ok, struct} -> "Updated"
                {:error, changeset} -> "can not update"
                end
            end

            def delete_task(id) do
                task = Repo.get!(TodoList.Task, id)
                case Repo.delete task do
                {:ok, struct} -> "Deleted #{id} numbered task"
                {:error, changeset} -> "Could not delete #{id} task"
                end
            end

            defp convert_to_map(task) do
                Map.from_struct(task)
            end

            defp drop_meta(task) do
                Map.drop(task, [:__meta__])
            end

            defp encode_poison(task) do
                Poison.encode!(task)
            end
            end

Now, we can boot up iex -S mix and run,

    > TodoList.Task.create_task("Work", "Work for elixir", "incomplete")

    > TodoList.Task.tasks

    >> [
    %TodoList.Task{
        __meta__: #Ecto.Schema.Metadata<:loaded, "tasks">,
        id: 1,
        inserted_at: ~N[2018-08-27 18:11:46.807061],
        task_description: "Work for elixir",
        task_name: "Work",
        task_status: "incomplete",
        updated_at: ~N[2018-08-27 18:11:46.811099]
    }
    ]



    > TodoList.Task.show_task(1) #id

    >> "{\"updated_at\":\"2018-08-27T18:11:46.811099\",\"task_status\":\"incomplete\",\"task_name\":\"Work\",\"task_description\":\"Work for elixir\",\"inserted_at\":\"2018-08-27T18:11:46.807061\",\"id\":1}"

    > TodoList.Task.update_task(1, %{task_name: "New Name"}) 
    #id, changeset

    >> "Updated"

    > TodoList.Task.delete_task(1) #id

    >> "Deleted 1 numbered task"

And this is a small CRUD based todolist made with mix project.

The github link of the full code is here: [Link](https://github.com/prio101/mix_todo_app) Of the Project.    


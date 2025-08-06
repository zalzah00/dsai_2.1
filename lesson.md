# Lesson

## Brief

### Preparation

Install conda environments required for the rest of module. Go to the `environments` folder and create the conda environments based on the `environment.yml` file. Each `yml` file is prefixed with the environment name. 

For example, to create the `bde` environment, first navigate into the `environments` folder by running `cd environments`, then run the following command:

`conda env create --file bde-environment.yml`

To replace an existing environment:

`conda env update --file bde-environment.yml --prune`

### For Windows WSL Users

If you get an error message when creating the `bde` environment, e.g.
> ERROR: Could not build wheels for thriftpy2, which is required to install pyproject.toml-based projects.

Run the following CLI command from your terminal:

`sudo apt install build-essential`

### Lesson Overview

This lesson introduces the concept of big data and data engineering. It also introduces one of the most popular NoSQL databases- MongoDB, and how to perform CRUD operations.

---

## Part 1 - Introduction to big data

Conceptual knowledge, refer to slides.

---

## Part 2 - Introduction to data engineering

Conceptual knowledge, refer to slides.

---

## Part 3 - Hands-on with MongoDB

We will be using the `notebooks/nosql_lesson.ipynb` notebook throughout this lesson.

> Open the notebook in VSCode by double clicking on the file. Then select `bde` conda environment for the kernel.
>
> Follow on with the lesson in the notebook.

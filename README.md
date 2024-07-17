# GCP Exam Materials

This repo contains the source Markdown files of the [GCP Exam Materials](https://borbalp.github.io/gcp-prep/index.html) book.

## Project Overview

This project uses [mdBook](https://github.com/rust-lang/mdBook) to generate a static site from Markdown files. The mdBook tool allows for easy creation, maintenance, and deployment of the book.

## How to Contribute

We welcome contributions! You can contribute by adding new content, refining existing notes, or updating outdated information. To contribute, follow these steps:

1. **Clone the Repository:**
    ```sh
    git clone https://github.com/borbalp/gcp-prep.git
    cd gcp-prep
    ```

2. **Install mdBook:**
    If you don't have `mdBook` installed, you can install it using Cargo (Rust's package manager, recommended to install using [rustup](https://rustup.rs/)):
    ```sh
    cargo install mdbook
    ```

3. **Serve the Book Locally:**
    To view the book locally while making changes, you can serve it using:
    ```sh
    mdbook serve
    ```
    This will start a local server and you can view the book at `http://localhost:3000`. The server will automatically reload when you make changes to the Markdown files.

4. **Build the Book:**
    To build the static site, run:
    ```sh
    mdbook build
    ```
    This will generate the static files in the `book` directory.

## Continuous Deployment

This project includes a pipeline that rebuilds and deploys the book on every push to the main branch. The pipeline is configured to automatically:

- **Rebuild the Book:** Every time you push changes to the repository, the pipeline will rebuild the book using mdBook.
- **Deploy the Book:** After rebuilding, the pipeline will deploy the updated version to GitHub Pages.

You can find the deployed version of the book [here](https://borbalp.github.io/gcp-prep/index.html).

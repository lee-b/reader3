# reader 3

![reader3](reader3.png)

A lightweight, self-hosted EPUB reader that lets you read through EPUB books one chapter at a time. This makes it very easy to copy paste the contents of a chapter to an LLM, to read along. Basically - get epub books (e.g. [Project Gutenberg](https://www.gutenberg.org/) has many), open them up in this reader, copy paste text around to your favorite LLM, and read together and along.

This project was 90% vibe coded just to illustrate how one can very easily [read books together with LLMs](https://x.com/karpathy/status/1990577951671509438). I'm not going to support it in any way, it's provided here as is for other people's inspiration and I don't intend to improve it. Code is ephemeral now and libraries are over, ask your LLM to change it in whatever way you like.

## Usage

The project uses [uv](https://docs.astral.sh/uv/). So for example, download [Dracula EPUB3](https://www.gutenberg.org/ebooks/345) to this directory as `data/dracula.epub`, then:

```bash
uv run reader3ctl add data/dracula.epub
```

This creates the directory `data/dracula_data`, which registers the book to your local library. We can then run the server:

```bash
uv run reader3-server
```

And visit [localhost:8123](http://localhost:8123/) to see your current Library. You can easily add more books, or delete them from your library by deleting the folder. It's not supposed to be complicated or complex.

## Docker and docker-compose

Rather than the uv commands and the reader3-server command above, you can build and run this via docker, as follows:

```bash
docker build -t reader3 .
docker run reader3
``

Alternatively, you can run it with docker compose, as follows:

```bash
docker compose up
```

This will do the building for you, without needing a manual uv installation, and may help you with integrating this into your home network. Don't run this on any commercial (or other) network where security is paramount, of course -- it's just not made for that.

In either docker use case, you can still connect to the service at [localhost:8123](http://localhost:8123/), as above.

## License

MIT

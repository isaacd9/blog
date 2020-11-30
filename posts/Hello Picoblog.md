# Hello Picoblog!
## The world's tiniest blogging platform
(maybe, I haven't checked)

![Blogging vs. blog setups](https://rakhim.org/images/honestly-undefined/blogging.jpg)

My name is Isaac. I'm an engineer at [Stripe](http://stripe.com/), where I
worked on high availability, disaster recovery, and compliance with
international data sovereignty rules. I've written a blogging platform. In
fact, it's where you're reading this blog post right now.

It's written in [Go](https://golang.org/) (you know, like):
```
func main() {
  fmt.Printf("hi there cruel world")
}
```

This blogging platform, called Picoblog, is _extremely simple_. Heavily
inspired on a project by my coworker [Seena](https://seenaburns.com/), called
[Picofeed](https://github.com/seenaburns/picofeed), it works by synthesizing a
list of blog posts into an HTML file and optional RSS feed. Blog posts are
written directly as Markdown, so they're easy to draft in your favorite editor
(or Dropbox Paper) and render out directly as HTML.

To specify a list of files to bloggify, simply write a file listing out the
locations of blog posts and the dates at which they were published:

```
posts/Hello Picoblog.md, 2020-11-29
```

And point `picoblog` at it. It'll generate
HTML to stdout. Redirect it to a file to host
it as a static site:
```
picoblog --list posts.txt > out.html
```

Post titles are set by the filename (without extension or path). The date is
set by updating the date above using the same format. The order of posts is
determined by their order in the file, making it possible to update the edited
date without causing an ordering conflict. Originally, I was just going to use the
modified time of the post, but this got annoying when fixing typos. Now you can
set it manually.

At time of writing, Picoblog's entire codebase is 279 lines of code, including
the template (not bad if I say so myself) (also this cheats a bit because it
uses Blackfriday as a renderer which is many more lines of code). That said,
It's pretty feature packed. It supports all of the syntax of Markdown, previews
(by generating a preview using the `./picoblog` CLI tool), and permalinks (by
referring to the `id` of the post title).

A reasonable question you might be asking yourself is: "Why did Isaac choose to
spend his time writing a teeny tiny blogging platform when so many great ones
already exist, like Jekyll, Hugo, and hosted ones like Svbtle?". I don't have a
good answer to that.

If you like the way `picoblog` looks and want to use it for yourself, the code
is here:
[https://github.com/isaacd9/picoblog](https://github.com/isaacd9/picoblog). I'd
be happy to take any pull requests against it.

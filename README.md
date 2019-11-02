## Blog built in Jekyll

**Requirements**

- Ruby 2.6+


**Setup**

1. Install Jekyll

```
gem install jekyll bundler
```

2. Create [Gem file](Gemfile)
3. Run `bundle`
4. Create the folders `_layouts` and `_posts`

To run locally execute

```
bundle exec jekyll serve
```

Then open `http://localhost:4000`

**New posts entry**

Create new `md` files in _posts folder using this format:

```
YYYY-MM-DD-<post-name>.md
```

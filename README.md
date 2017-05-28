# sous-chefs.org

The website is created using the static site generator, [Hugo](https://gohugo.io/).

## Development

1. Install Hugo for your platform according to the [instructions](http://gohugo.io/overview/installing/)
  * For MacOS, you can use Homebrew: `brew install hugo`
  * For Windows, follow the instructions at [http://gohugo.io/tutorials/installing-on-windows/](http://gohugo.io/tutorials/installing-on-windows/)
2. Create a feature branch to work on based off of `master`
3. Clone the website code and start the development server. This will run a local hugo server that watches for changes to the source files. There will be a section in the output showing which port the site is served on (typically http://localhost:1313)
        git clone git@github.com:sous-chefs/website
        cd website
        hugo server -ws .
4. Push the branch to the remote and open a Pull Request.

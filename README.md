# uacnc-website

This is the repository for the UACNC Website, as of 2022.

Jekyll is used to generate static webpages for the website.

Jekyll affords UACNC advantages in many ways:
* Little manual coding is needed
* Website content is written using Markdown, making content creation accessible to members with non-technical backgrounds
* The website can be hosted for free on many providers such as GitHub pages, unlike its competitors which require expensive subscription plans
* Jekyll can be used on macOS, GNU/Linux and Windows, and is not tied to any specific operating system
* Jekyll is free/libre and open-source, released under the permissive MIT License

The process of running the website can be simplifed into three steps:
1. Write
2. Build
3. Serve

Writing content can be done by most people with non-technical backgrounds.  Website pages and blogposts are written using Markdown, making the website accessible to anyone in the UACNC team, especially outside the tech team.  There are many apps that support Markdown from the get go, and even support syntax highlighting.  For starters, Visual Studio Code or Sublime Text support syntax highlighting, and the former can be configured to additionally perform syntactic checks.  On the other hand, if one would rather not install a text editor for editing Markdown files, there are other Markdown-dedicated options out there.  One example is the Typewriter app available on macOS, iPadOS and iOS.

Once the Markdown files that bear the blog posts have been added or updated, the website is then built with Jekyll.  This causes Jekyll to parse the Markdown files and generate the static webpage content in HTML to allow the website to be viewed on a browser.  Additionally, the HTML are themed with CSS based on Jekyll themes.

Finally, the generated Jekyll website is then served by a server.  In short, the website becomes accessible to users only with a web browser.

Please look at the "Running" section for more information about the three-step process.

## SET UP DEVELOPMENT ENVIRONMENT
### Pre-Requisites
* Ruby version 2.5.0 or higher
* RubyGems
* GNU Compiler Collection (GCC)
* Make

You can verify the installation of the pre-requisites by entering the following commands in your terminal:
```sh
# Ruby
ruby -v

# RubyGems
gems -v

# C++ Compiler, such as GNU Compiler Collection (GCC)
# (on macOS, the commands below may use Apple Clang instead)
gcc -v
g++ -v

# Make
make -v
```

### Installation (macOS 12.6, Apple Silicon)
The instructions on the official Jekyll website may or may not work depending on your setup.

The instructions outlined in this section works on an Apple Silicon machine.

The instructions were adapted from [https://utpalkumar.medium.com/how-to-install-jekyll-on-apple-m1-macbook-c87894b7fc70](https://utpalkumar.medium.com/how-to-install-jekyll-on-apple-m1-macbook-c87894b7fc70).

Note that it is assumed that the Command Line Developer Tools from Xcode have already been installed.

First, install a Ruby version compatible with the ARM processor.  Note that `rbenv` does not come with the `install` command by default.  The package `ruby-build` will add the `install` command to `rbenv`.
```sh
# Homebrew
brew install rbenv
# MacPorts
sudo port install rbenv ruby-build
```

Next, install an ARM-based version of Ruby.  As of the time of writing, version 3.1.2 is the current stable version:
```sh
rbenv install 3.1.2  # takes some time
rbenv global 3.1.2
```

Next, add `rbenv` to your shell so that it loads every time a terminal window is opened:
```sh
# ZSH
echo 'eval "$(rbenv init - zsh)"' >> ~/.zshrc
# Bash
echo 'eval "$(rbenv init - bash)"' >> ~/.bash_profile
```

Then close your terminal and open it again, entering the following commands in the new session:
```sh
ruby -v
rbenv rehash
```

`ruby -v` should show the version of Ruby you have installed, e.g.:
```sh
ruby 3.1.2p20 (2022-04-12 revision 4491bb740a) [arm64-darwin21].
```

Finally, install Jekyll and Bundler:
```sh
gem install bundler jekyll
```

### Installation (Ubuntu 22.04 LTS)
Install the prerequisites:
```sh
sudo apt install ruby-full build-essential zlib1g-dev
```

It is not recommended to install RubyGems as the root user.  Instead, set up a `gem` installation directory in your home directory instead as a non-root user.  This step should automatically be done for you upon installation of RubyGems and running `gems -v` as above.

Next, add RubyGems and any binaries that it installs to the path:
```sh
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

Finally, install Jekyll and Bundler:
```sh
gem install jekyll bundler
```

## RUNNING THE WEBSITE
### Write
TODO: Write about file structure, i.e. where to add Markdown files.

### Build
The website can be built by running the following command in the working directory of the website:
```sh
bundle exec jekyll build
```

Optionally, one can use the shorthand `b` subcommand instead of `build`:
```sh
bundle exec jekyll b
```

### Serve
Finally, the website can be served on one's computer with the following command:
```sh
bundle exec jekyll serve
```

Optionally, one can use the shorthand `s` subcommand instead of `server`:
```sh
bundle exec jekyll s
```

Serving the website is particularly useful for when testing the website during development phase.

In production, instructions are provided by the host (e.g. GitHub Pages) to serve the website.

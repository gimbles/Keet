# Keet
✨ A minimal, tiny and easy to use build system for Unix-like OSs made with <3 and Ruby!

# Installation
Using Keet is really simple, you just clone the file and chuck it in your projects root folder, it's design is minimal and straight to the point. You simply add your profiles and commands to the script and.. congrats! You have now successfully added parakeet to your project :)      
      
Here's a handy command to install it in your project! - `wget https://raw.githubusercontent.com/Yush08/Keet/main/keet` 

# Configuration
Configuring Keet doesn't require any knowledge of the Ruby language, even though it may seem like it at first. Here's an example!

```ruby
GREET = "Welcome to the Zen build system"

COMMANDS = {
  "r" => {
    "description" => "Debug run.",
    "Darwin|Linux" => ["cargo run"],
  },

  "rr" => {
    "description" => "Release run.",
    "Darwin|Linux" => ["cargo run --release"],
  },

  "b" => {
    "description" => "Debug build.",
    "Darwin|Linux" => ["cargo build"],
  },

  "rb" => {
    "description" => "Release build.",
    "Darwin|Linux" => ["cargo build --release"],
  },

  "prod" => {
    "description" => "Production build.",
    "Darwin" => ["cargo +nightly build -Z build-std=std,panic_abort -Z build-std-features=panic_immediate_abort --target aarch64-apple-darwin --release",
                 "strip target/aarch64-apple-darwin/release/zen"],

    "Linux" => ["cargo +nightly build -Z build-std=std,panic_abort -Z build-std-features=panic_immediate_abort --target x86_64-unknown-linux-gnu --release",
                "strip target/x86_64-unknown-linux-gnu/release/zen"],
  },

  "fmt" => {
    "description" => "Format code.",
    "Darwin|Linux" => ["cargo fmt"],
  },

  "cls" => {
    "description" => "Clean workspace.",
    "Darwin|Linux" => ["cargo clean"],
  },

  "chk" => {
    "description" => "Check code for errors.",
    "Darwin|Linux" => ["cargo check"],
  },

  "clp" => {
    "description" => "Linter.",
    "Darwin|Linux" => ["cargo clippy"],
  },
}

```

The `GREET` variable is is the welcome message. This line is the first line that is printed by the build system.               
        
The `COMMANDS` variable defines what commands the build system should run when the user requests a profile. It's a HashMap, also known as a dictionary. Each profile holds a description and different operating systems. The operating system is fetched from `uname -s`. You may use regex as shown above in the example. Each operating system holds a list of commands to run.     
     
The build system will look for a "KeetConf" file storing this configuration and evaluate it accordingly. Place this file in the same position as parakeet.

## Fancy configuration
Fear not my friend! The configuration is *comlpetely* turing complete as it is just Ruby code in the end! Parakeet will simply evaluate the file and you can use all the fancy Ruby code you want.
___

# License
This project is licensed under the MIT license.

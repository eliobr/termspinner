# spinner

A simple terminal spinner written in crystal

## Installation

1. Add the dependency to your `shard.yml`:

   ```yaml
   dependencies:
     termspinner:
       github: eliobr/termspinner
   ```

2. Run `shards install`

## Usage

```crystal
require "termspinner"
```

```crystal
spi = Spinner::Spinner.new("Waiting...")
begin
  spi.start()
  response = HTTP::Client.get("https://cataas.com/cat/gif")
  if response.status_code == 200
    spi.success("Success")
  else
    spi.error("Failed")
  end
rescue
  spi.error("Error while trying to connect")
end
spi.start("Doing something useful...")
sleep(2.seconds)
spi.message= "The process is taking longer than expected..."
sleep(3)
spi.error("Failed to do something useful")
spi.start("Doing something...")
sleep(2.seconds)
spi.stop("⚠️  Some custom message".colorize(:yellow).to_s)
```
![](https://raw.githubusercontent.com/eliobr/termspinner/master/example.svg?sanitize=true)

## Contributing

1. Fork it (<https://github.com/eliobr/termspinner/fork>)
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request

## Contributors

- [elio](https://github.com/eliobr) - creator and maintainer

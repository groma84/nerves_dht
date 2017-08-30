# Nerves DHT

Elixir library to read the DHT series of humidity and temperature sensors on a Raspberry Pi.
The library is supposed to be included in a [nerves project](http://nerves-project.org/).

If you want to build your project directly on a Raspberry (not in a crosscompiling nerves project)
just export MIX_TARGET environment variable to you mix build.
Valid values for MIX_TARGET are rpi | rp2 | rp3.

* Supported sensors: DHT11, DHT22, AM2302
* Supported boards: Raspberry 1 / 2 / 3

Note: the library has no external dependencies and use a C executable to read the sensors data.

## Installation

The package can be installed by adding `nerves_dht` to your list of dependencies in `mix.exs`:

```elixir
def deps do
  [
    {:nerves_dht, git: "https://github.com/visciang/nerves_dht.git", "tag: 1.0.0"}
  ]
end
```

## Usage

```elixir
iex> Nerves.DHT.read(:am2302, 17)
{:ok, 55.1, 24.719}

iex> Nerves.DHT.stream(:am2302, 17) |> Enum.take(2)
[{:ok, 55.1, 24.719}, {:ok, 55.12, 24.9}]
```
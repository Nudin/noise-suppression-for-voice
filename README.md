# Real-time Noise Suppression Plugin (LADSPA) for mpv

A real-time noise suppression plugin for voice based on [Xiph's RNNoise](https://github.com/xiph/rnnoise). [More info about the base library](https://people.xiph.org/~jm/demo/rnnoise/).

Repo from @werman changed minimally based on input form @tobia to run with [mpv](https://mpv.io/).

## About

The plugin is meant to suppress a wide range of noise origins ([from original paper](https://arxiv.org/pdf/1709.08243.pdf)): computer fans, office, crowd, airplane, car, train, construction. 

From my tests mild background noise is always suppressed, loud sounds, like clicking of mechanical keyboard, are suppressed while there is no voice however they are only reduced in volume when voice is present. 

The plugin is made to work with 1 channel, 16 bit, 48000 Hz audio input. Other sample rates may work, or not...

## How-to

### MPV
To use with the mpv player build it:
```
$ cmake .
$ make -j
$ cp bin/x64/ladspa/librnnoise_ladspa_x64.so ~/.local/lib/ladspa/rnnoise.so
```

You then need to add it to the `LADSPA_PATH`, for example by adding the following to your `~/.profile`:
```
export LADSPA_PATH=~/.local/lib/ladspa
```

The you can map any key in your configuration to toggle noise-suppression, by adding it to your `~/.mpv/input.conf`:
```
N af toggle ladspa=rnnoise:noise_suppressor
```

## License

This project is licensed under the GNU General Public License v3.0 - see the LICENSE file for details.

# Challenge Name:
 [*Monaliza*](https://cybertalents.com/challenges/forensics/monaliza)
 
# Challenge Description
We cannot identify this suspicious user behavior, but we know he is a big fan of Monaliza

Link: [https://hubchallenges.s3-eu-west-1.amazonaws.com/Forensics/monaliza.7z](https://hubchallenges.s3-eu-west-1.amazonaws.com/Forensics/monaliza.7z)

## Answer
* Download the file
* Unzip it as follow
```sh
7z e monaliza.7z
```
* We want to know file type so run file then cat to see it's content
```sh
file monaliza.mem
cat monaliza.mem
```
* There are alot of lines in this file we can't see it all of course
* Grep specific pattern from this file content
```sh
strings monaliza.mem | grep "Flag{"
```
* You got the Flag


 ## The Flag
 > Flag{i_w!ll_d3l3t3_my_s3cret}



Stegsolve Interactively transform images, view color schemes separately

SonicVisualiser Visualizing audio files in waveform, display spectrograms

DeepSound Audio stego tool that was used in Mr. Robot series. Windows tool but could be run in wine

Steghide tool to encrypt and hide data.
sox tool . 
volatility

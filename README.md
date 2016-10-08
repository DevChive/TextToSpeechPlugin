## Text To Speech Plugin for Xamarin and Windows

Simple and elegant way of performing Text To Speech across Xamarin.iOS, Xamarin.Android, Windows, and Xamarin.Forms projects.

Preview: http://screencast.com/t/voW1P48Ka


### Setup
* Available on NuGet: https://www.nuget.org/packages/Xam.Plugins.TextToSpeech/ [![NuGet](https://img.shields.io/nuget/v/Xam.Plugins.TextToSpeech.svg?label=NuGet)](https://www.nuget.org/packages/Xam.Plugins.TextToSpeech/)
* **Install into your PCL project and Client projects**.

Build status: 
* [![Build status](https://ci.appveyor.com/api/projects/status/ucwvippb5awrsqmg?svg=true)](https://ci.appveyor.com/project/JamesMontemagno/texttospeechplugin)
* CI NuGet Feed: https://ci.appveyor.com/nuget/texttospeechplugin

**Platform Support**

|Platform|Supported|Version|
| ------------------- | :-----------: | :------------------: |
|Xamarin.iOS|Yes|iOS 7+|
|Xamarin.iOS Unified|Yes|iOS 7+|
|Xamarin.Android|Yes|API 10+|
|Windows Phone Silverlight|Yes|8.0+|
|Windows Phone RT|Yes|8.1+|
|Windows Store RT|Yes|8.1+|
|Windows 10 UWP|Yes|10+|
|Xamarin.Mac|No||


### Features
* Speak back text
* Pitch
* Volume
* Speak Rate
* Locale/Language of Speech
* Gather all available languages to speak in

### Usage

**Simple Text**
```csharp
await CrossTextToSpeech.Current.Speak("Text to speak");
```

**Advanced speech API**
```csharp
/// <summary>
/// Speack back text
/// </summary>
/// <param name="text">Text to speak</param>
/// <param name="crossLocale">Locale of voice</param>
/// <param name="pitch">Pitch of voice (All 0.0 - 2.0f)</param>
/// <param name="speakRate">Speak Rate of voice (All) (0.0 - 2.0f)</param>
/// <param name="volume">Volume of voice (iOS/WP) (0.0-1.0)</param>
/// <param name="cancelToken">Cancel the current speech</param>
public async Task Speak(string text, CrossLocale crossLocale = null, float? pitch = null, float? speakRate = null, float? volume = null, CancellationToken? cancelToken = null)
```  

**CrossLocale**
I developed the CrossLocale struct mostly to support Android, but is nice because I added a Display Name.

You can query a list of current support CrossLocales on the device:

```csharp
/// <summary>
/// Get all installed and valide lanaguages
/// </summary>
/// <returns>List of CrossLocales</returns>
public IEnumerable<CrossLocale> GetInstalledLanguages()
```

Each local has the Language and Display Name. The Country code is only used in Android. If you pass in null to Speak it will use the default.

#### Implementation

* iOS: AVSpeechSynthesizer
* Android: Android.Speech.Tts.TextToSpeech
* Windows: SpeechSynthesizer + Ssml support for advanced playback


**Windows Phone**
You must add ID_CAP_SPEECH_RECOGNITION permission


### Branches
Main branch is always the current development beta branch. This means that all new work can be done off this branch. For each release of a stable NuGet package a new release branch will be created so any additional hot fixes could be done off of that branch.

### Contributions
Contributions are welcome! If you find a bug please report it and if you want a feature please report it.

If you want to contribute code please file an issue first and mark that you will be working on it so we can figure out a release path. The flow should go:

1. Create an issue
2. Fork project
3. Create branch off of master (or the branch that needs a hot fix)
4. Send pull request to the branch that code should be merged in (ensuring that you mark the issue that it is fixing)

#### License
Under MIT, see LICENSE file.

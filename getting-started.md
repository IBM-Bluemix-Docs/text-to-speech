---

copyright:
  years: 2015, 2021
lastupdated: "2021-02-09"

keywords: text to speech,IBM cloud,getting started,tutorial,synthesize audio,speech synthesis

subcollection: text-to-speech

content-type: tutorial
account-plan: lite
completion-time: 10m

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:go: .ph data-hd-programlang='go'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}
{:hide-dashboard: .hide-dashboard}
{:step: data-tutorial-type='step'}
{:video: .video}

# Getting started with {{site.data.keyword.texttospeechshort}}
{: #gettingStarted}
{: toc-content-type="tutorial"}
{: toc-completion-time="10m"}

The {{site.data.keyword.texttospeechfull}} service converts written text to natural-sounding speech to provide speech-synthesis capabilities for applications. This curl-based tutorial can help you get started quickly with the service. The examples show you how to call the service's `POST` and `GET /v1/synthesize` methods to request an audio stream.
{: shortdesc}

Watch the following video for a visual summary of getting started with the {{site.data.keyword.texttospeechshort}} service. The video shows the steps described in the following sections.

![Getting started with the {{site.data.keyword.texttospeechshort}} service](https://video.ibm.com/embed/channel/23952663/video/text-to-speech-get-started){: video output="iframe" data-script="none" id="watsonmediaplayer" width="560" height="315" scrolling="no" allowfullscreen webkitallowfullscreen mozAllowFullScreen frameborder="0" style="border: 0 none transparent;"}

## Before you begin
{: #before-you-begin}

- {: hide-dashboard}  Create an instance of the service:
    1.  {: hide-dashboard} Go to the [{{site.data.keyword.texttospeechshort}}](https://{DomainName}/catalog/services/text-to-speech){: external} page in the {{site.data.keyword.cloud_notm}} Catalog.
    1.  {: hide-dashboard} Sign up for a free {{site.data.keyword.cloud_notm}} account or log in.
    1.  {: hide-dashboard} Click **Create**.
-   Copy the credentials to authenticate to your service instance:
    1.  {: hide-dashboard} From the [{{site.data.keyword.cloud_notm}} Resource list](https://{DomainName}/resources){: external}, click on your {{site.data.keyword.texttospeechshort}} service instance to go to the {{site.data.keyword.texttospeechshort}} service dashboard page.
    1.  On the **Manage** page, click **Show Credentials** to view your credentials.
    1.  Copy the `API Key` and `URL` values.

### Using the curl examples
{: #getting-started-curl}

This tutorial uses the `curl` command to call methods of the service's HTTP interface. Make sure that you have the `curl` command installed on your system.

1.  To test whether `curl` is installed, run the following command on the command line. If the output lists the `curl` version that supports Secure Sockets Layer (SSL), you are set for the tutorial.

    ```bash
    curl -V
    ```
    {: pre}

1.  If necessary, install the version of `curl` with SSL enabled for your operating system from [curl.haxx.se](https://curl.haxx.se/){: external}.

Omit the braces (`{ }`) from the examples. They indicate variable values.
{: tip}

## Synthesize text in US English
{: #synthesizeEnglish}
{: step}

The following commands use the `POST /v1/synthesize` method to synthesize US English input to audio files in two different formats. Both requests use the default US English voice, `en-US_MichaelV3Voice`.

1.  Issue the following command to synthesize the string "hello world" and produce a WAV file that is named `hello_world.wav`.
    -   {: hide-dashboard} Replace `{apikey}` and `{url}` with your API key and URL.

    *Windows users,* replace the backslash (`\`) at the end of each line with a caret (`^`). Make sure there are no trailing spaces.
    {: tip}

    ```bash
    curl -X POST -u "apikey:{apikey}"{: apikey} \
    --header "Content-Type: application/json" \
    --header "Accept: audio/wav" \
    --data "{\"text\":\"hello world\"}" \
    --output hello_world.wav \
    "{url}/v1/synthesize"{: url}
    ```
    {: pre}

1.  Issue the following command to synthesize the same text but produce an Ogg file (the default format) that is named `hello_world.ogg`.
    -   {: hide-dashboard} Replace `{apikey}` and `{url}` with your API key and URL.

    ```bash
    curl -X POST -u "apikey:{apikey}"{: apikey} \
    --header "Content-Type: application/json" \
    --data "{\"text\":\"hello world\"}" \
    --output hello_world.ogg \
    "{url}/v1/synthesize"{: url}
    ```
    {: pre}

You can use a browser or other tools to play the audio files that are produced by the examples in this tutorial. For more information, see [Playing an audio file](/docs/text-to-speech?topic=text-to-speech-audioFormats#formatsPlay).
{: note}

## Synthesize text in Spanish
{: #synthesizeSpanish}
{: step}

The following command uses the `GET /v1/synthesize` method to synthesize Spanish input to an audio file.

1.  Issue the following command to synthesize the string "hola mundo" and produce a WAV file that is named `hola_mundo.wav`. The input text is URL-encoded. The method includes the query parameters `accept` to specify the audio format and `voice` to specify a Spanish voice, `es-ES_EnriqueV3Voice`.
    -   {: hide-dashboard} Replace `{apikey}` and `{url}` with your API key and URL.

    ```bash
    curl -X GET -u "apikey:{apikey}"{: apikey} \
    --output hola_mundo.wav \
    "{url}/v1/synthesize?accept=audio%2Fwav&text=hola%20mundo&voice=es-ES_EnriqueV3Voice"{: url}
    ```
    {: pre}

## Next steps

-   To try an example application that accepts text and generates speech with different voices, see the [{{site.data.keyword.texttospeechshort}} demo](https://www.ibm.com/demos/live/tts-demo/self-service/home){: external}.
-   For more information about the service's interfaces and features, see [Service features](/docs/text-to-speech?topic=text-to-speech-service-features).
-   For more information about all methods of the service's interfaces, see the [API & SDK reference](https://{DomainName}/apidocs/text-to-speech){: external}.

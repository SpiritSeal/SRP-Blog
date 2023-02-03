
## Description
This project addresses the systemic vulnerabilities of modern, unrestricted, executable-based plugin frameworks with a focus on those that leverage or encourage 3rd party plugin manufacturers. The goals of this project are to build extendable proof-of-concepts that can identify existing abuses of the technology and prevent further exploitation in the future.

# Abstract

In the current era of technology, extendibility has become a ubiquitous feature of modern software. Many applications, ranging from web browsers, to image editors, to office softwares and beyond, have grown to offer the ability to add custom functionality through the use of extensions.

The popularity of third-party plugin systems has also skyrocketed in recent years, leading to a proliferation of these tools across a wide range of software platforms. However, by encouraging third parties to develop and release plugins in this manner, developers of these host applications have effectively opened the door for bad actors to take advantage of these interfaces to attack consumer devices through the arbitrary code execution these plugin systems enable.

And as such, over the last two decades, industry engineers and cybersecurity researchers alike have been constructing and iterating security measures that prevent such framework exploitation. A dominant and effective mitigation technique requires plugin developers to declare the specific additional permissions they would like their plugin to utilizing, rendering the add-on physically incapable of performing actions outside of the scope explicity authorized by the end user. As successful as this technique may be for mitigating and preventing attack surface, it relies on plugins to be created with interpreted programming language, such as JavaScript, which execute substantially slower than their compiled counterparts, making this security system inviable in many speed-critical environments, such as those involving realtime media manipulation (ex: 3D modeling, music production, video editing, etc.).

This project seeks to build proactive and retroactive solutions that can enable this powerfully effective permission declaration to plugin systems that are compiled directly and shipped as machine code.

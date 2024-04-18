# RFC-1100/TariUniverseDevMode

## Tari Universe Developer Mode

![status: draft](theme/images/status-draft.svg)

**Maintainer(s)**: [Maciej Kożuszek](https://github.com/MCozhusheck)

# Licence

[ The 3-Clause BSD Licence](https://opensource.org/licenses/BSD-3-Clause).

Copyright 2024 The Tari Development Community

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the
following conditions are met:

1. Redistributions of this document must retain the above copyright notice, this list of conditions and the following
   disclaimer.
2. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following
   disclaimer in the documentation and/or other materials provided with the distribution.
3. Neither the name of the copyright holder nor the names of its contributors may be used to endorse or promote products
   derived from this software without specific prior written permission.

THIS DOCUMENT IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS", AND ANY EXPRESS OR IMPLIED WARRANTIES,
INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
SPECIAL, EXEMPLARY OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
SERVICES; LOSS OF USE, DATA OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY,
WHETHER IN CONTRACT, STRICT LIABILITY OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF
THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

## Language

The keywords "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED",
"NOT RECOMMENDED", "MAY" and "OPTIONAL" in this document are to be interpreted as described in
[BCP 14](https://tools.ietf.org/html/bcp14) (covering RFC2119 and RFC8174) when, and only when, they appear in all capitals, as
shown here.

## Disclaimer

This document and its content are intended for information purposes only and may be subject to change or update
without notice.

This document may include preliminary concepts that may or may not be in the process of being developed by the Tari
community. The release of this document is intended solely for review and discussion by the community regarding the
technological merits of the potential system outlined herein.

## Goals

This RFC describes how the tapplet developers will be able to manually test and verify their tapplets in Tari Universe.

## Related Requests for Comment

- [RFC-1101: Tapplet](https://github.com/tari-project/rfcs/pull/137)
- [RFC-1106: Tapplet Installation](https://github.com/karczuRF/tari-rfcs/blob/feat/rfc-tapplet_installation/src/RFC-1106_TappletInstallation.md)

## Problem of testing tapplets

In contrary to web development testing is pretty straightforward - there are plenty tools to build and serve locally project (like babel or vite) and developers can play around by simply viewing them in the browser that also has debug tools.

In a case of tapplet it is impossible as tapplets requires to import dependencies that relies on tauri like `import { invoke } from "@tauri-apps/api/core";` that is crucial for provider but won't work inside web browser.

## General Solution

To address this problem Tari Universe should enable a `developer mode` where developer can locally upload their work in progress tapplet to the Tari Universe. In a similar manner web browsers also allows to locally test extensions where developer after enabling `developer mode` can upload their extensions.

## Web browser approach

In a case of chrome web browsers it requires to provide a unpacked extension where from now on browser handles loading it to the browser and displaying. It is inconvenient as developer needs to rebuild and upload again extension over any change.

## Proposed approach

Tari Universe displays tapplets using `<iframe>` which make very simple to display locally hosted tapplets. We can use this to simplify developing process by simply providing port of the self hosted tapplet which also enables hot-reloading - developer no longer needs to build project and upload them again.

## UX of enabling developer mode

This feature should be somewhere at the bottom of settings where casual users won't notice as much.
After enabling it, in the tapplet list there should popup new button that reads "Upload tapplet" and after clicking it users can specify folder containing valid tapplet structure. This new tapplet should be displayed on the list available tapplets with a icon indicating that it's locally imported one.

# References

[How to test a chrome extension](https://medium.com/@aabroo.jalil/how-to-test-a-chrome-extension-locally-step-by-step-guide-852e4622d4c7)

# Change Log

| Date        | Change | Author      |
| :---------- | :----- | :---------- |
| 18 Apr 2024 | Draft  | MCozhusheck |

# TrackSearcher
Android library for getting full information about music track by track title.
## Features
- Parsing of data from ITunes, SoundCloud, last.fm
- Opportunity using custom parsers
- Caching (coming soon)

## Setup
Gradle:
```gradle
compile 'io.github.allockye:tracksearcher:1.2'
```
Maven:
```xml
<dependency>
  <groupId>io.github.allockye</groupId>
  <artifactId>tracksearcher</artifactId>
  <version>1.2</version>
  <type>pom</type>
</dependency>
```
## Usage
Before calling ```search``` you should to add at least one parser ```addParser```
```java
TrackSearcher trackSearcher = new TrackSearcher();
trackSearcher.addParser(new ITunesParser());
trackSearcher.addParser(new LastFmParser("YOUR_CLIENT_ID"));
trackSearcher.addParser(new SoundCloudParser("YOUR_CLIENT_ID"));
trackSearcher.search("Night Lovell", "Dark Light", new TrackSearcher.Callback() {
    @Override
    public void onSuccess(Track track) {
        // some code
    }

    @Override
    public void onFailure() {
        // some code
    }
});
```
## Custom parser
Implement interface ```Parser```
```java
class CustomParser implements Parser {
    @Override
    public Track parse(String artistName, String trackName) {
        // some code
        return null;
    }
}
```
## License
```
Copyright 2016 Alexey Elisov

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

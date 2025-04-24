## Rationale
As I've told you, this class got its start with Amy Schulz Johnson asking my colleagues in [ODH](https://odh.byu.edu) to help her do some analysis of her dad's work. Those colleagues created a corpus of _Peanuts_ by harvesting data from [GoComics.com](https://gocomics.com). The GoComics team has created transcripts of what happens in the comics, which are tremendously helpful. But...it turns out they're not always exactly correct. Just take a look at Schulz's comic for [Schulz's comic for 23 January 1952](https://www.gocomics.com/peanuts/1952/01/23) and GoComics's corresponding `data transcript`:

![Image of 23 January 1952 Peanuts strip](https://assets.amuniversal.com/c51df360f868013014ce001dd8b71c47)

> Schroeder sits at the piano playing. Charlie Brown comes up to him and says, "Say, that's sensational, Schroeder...what is it?" He looks to the reader confused as Schroeder replies, "Grasse Sonata fur das Hommer-Klavier" As Schroeder resumes his playing, Charlie Brown walks away. The latter says, "Sometimes I feel like I don't belong around here!"

So it's close...but it's maybe not close enough. There's a lot of information that isn't captured in this transcript: what music Schroeder is playing and all its attendant information; what happens in which panel; the question mark that Charlie Brown "speaks"; the McCloudian transitions (see chapter 3) across the gutters; and how Schulz signs his name. And that's just the first five things I thought to type! What's more, there are typos! It's very clear in the comic that Schroeder says "Grosse Sonata für das Hammer-Klavier" and not "Grasse Sonata fur das Hommer-Klavier"! Apparently whoever transcribed this comic wasn't used to reading [Fraktur](https://en.wikipedia.org/wiki/Fraktur).

We can do better than this! Creating marked-up editions of Peanuts strips will provide us the chance to more accurately represent the strip, as well as enriching it in the specific ways that we care about: settings, place names, weather, activities, the [Bechdel test](https://en.wikipedia.org/wiki/Bechdel_test), and pretty much anything else you can imagine. Creating such editions is time-consuming and requires serious attention to detail. But the opportunities for research that we gain with this process makes it worth the investment. To [quote John A. Walsh](http://www.digitalhumanities.org/dhq/vol/6/1/000117/000117.html), encoding *Peanuts* will "facilitate both close and distant reading strategies" (par. 17).

[removed class specific information here]

### Encode the strip
Encode the strip as follows. If you run into questions, be sure to refer to our "[Peanuts Encoding Editorial Decisions](https://docs.google.com/document/d/1qVETW1qeX1PRrFgswQY8uTrkPC8nWq9YIF2q99dvDj4/edit?usp=sharing)" document. Or watch the (coming-soon) following video!

Don't be alarmed at the size of this list. For most of the strips we encounter, many of these possibilities simply won't occur.

#### teiHeader
Since we will each have our own personalized template to work from, we won't have to make too many changes to the header. However, you _will_ need to update your template when we move from the 1961-1962 volume to the 1981-1982 volume (specifically <title> and <date> on line 40).

For each strip, however, you still need to make the following changes in the header:

1. <title> (line 11): Change the title to have the correct date in YYYY-MM-DD format
2. <idno> (line 35): Set the date to the proper YYYY-MM-DD format. Please make sure you don’t put a space between Peanuts and the year.
3. <title level='a'> (line 40): Change the date of the strip to the proper date in YYYY-MM-DD format.
4. <change> (line 68): for the value of `@who`, use your `r-name` from the taxonomy. For the value of when, record the date you are doing the edits using YYYY-MM-DD format. You’ll note that the description of the change is “Initial encoding.” If what you’re doing does not match that description, replace that phrase with a short description of what you’re doing. 
5. <graphic> (line 74): update the value of `@url` to the proper date for your comic. Open the URL in a browser (hold Ctrl/Cmd while clicking on it) to make sure it resolves properly.

**N.B. Please note that you can accomplish the first three by using Find/Replace (`Ctrl/Cmd-F`) and replacing YYYY-MM-DD with the proper date and then clicking `Replace All`.**

#### Body
Most of the work that you will do for each strip is in the <body> portion of the document. I suggest working on one aspect of the strip at a time (e.g., speech balloons or transitions) rather than moving through the strip like you are reading it.

Do the following 13 (!?!) things for each strip:

##### Metadata
1\. <head> (line 80): Change the date within the element to `(D)D [full month name] YYYY` format.

##### Weather, Activities, Settings, Holidays, Visual Aspects, Bechdel Test, and Story Arcs
2\. <div type="panelGrp"> (line 82): For each strip, tag weather, activities, settings, holidays, visual aspects, story arcs, and the Bechdel test using the `@ana` element. For a full list of the different options, see our [Editorial Decisions Document](https://docs.google.com/document/d/1qVETW1qeX1PRrFgswQY8uTrkPC8nWq9YIF2q99dvDj4/edit#heading=h.sgkh3p4tf5r7).

##### Number of Panels
3\. The template has a default of 4 panels. If there are more or less panels, add or subtract <cbml:panel> elements and number them properly using the `@n` attribute.

##### Characters in Panels
4\. <cbml:panel> (lines 84, 91, 96, and 101): For each panel, set the value of `@characters` that appear in that panel to the shortcodes of character names from [the taxonomy](https://github.com/briancroxall/peanuts-taxonomy/blob/master/peanuts-taxonomy.xml). Separate multiple character names with a space, e.g. `characters="#c-cb #c-lucy #c-violet"`.

##### Description of the Panel's Action
5\. <note> (lines 85, 92, 97, and 102): For each panel, set the value of `@resp` to your `r-name` from the [taxonomy](https://github.com/briancroxall/peanuts-taxonomy/blob/master/peanuts-taxonomy.xml). Within the element, write a _brief_ description of what happens in the panel. See the [1950](https://github.com/briancroxall/peanuts/blob/master/test/peanuts_1950_10_02.xml) and [1982](https://github.com/briancroxall/peanuts/blob/master/test/peanuts_1982_02_13.xml) examples in the [`xml-test` folder](https://github.com/briancroxall/peanuts/tree/master/xml-test) within the repo for ideas.

##### Speech and Sound
6\. <cbml:balloon>: Use this element to transcribe each speech act. Change the value of the `@type` attribute to [another choice](https://docs.google.com/document/d/1qVETW1qeX1PRrFgswQY8uTrkPC8nWq9YIF2q99dvDj4/edit#heading=h.z9fvl6dyavim) if it's not a normal speech balloon. Set the value of the `@who` attribute to the appropriate character name from the [taxonomy](https://github.com/briancroxall/peanuts-taxonomy/blob/master/peanuts-taxonomy.xml).
  - By default, the template is set up for a single speech balloon per panel. If there are multiple speech balloons in a panel, add additional <cbml:balloon> elements.
7\. If characters are referred by name or by nickname (e.g., "Chuck") in a speech bubble, wrap the name in a <persName> element and use a `@ref` attribute with the value set to the taxonomy reference; for example, <persName ref="#c-cb">.
8\. If real people are referred to by name (e.g., Beethoven, Peggy Fleming), tag them using a <persName> element and use a `@ref` attribute with the value set to a URI from an authority file like [VIAF](https://viaf.org/). For example, <persName ref="https://viaf.org/viaf/32182557/">Beethoven</persName>. You can often find such URIs under the `Authority Control` section of a person's [Wikipedia](https://en.wikipedia.org/wiki/Main_Page) entry.
9\. If real places are referred to by name (e.g., New York City), tag them using a <placeName> element and use a `@ref` attribute with the value set to a URI from an authority file like [GeoNames](https://www.geonames.org/).
10\. <sound>: Use this element to encode sounds that are not contained in a speech balloon (see [this example](https://www.gocomics.com/peanuts/1952/05/04)). This element should go on a new line within the <cbml:panel> and _**not**_ within the <cbml:balloon>. This element should _also_ be used to record onomatopoeic sounds within speech balloons.

##### Diegetic Text
11\. Text that would be visible to characters within the strip, such as [words on signs](https://www.gocomics.com/peanuts/1950/10/07) should be tagged in the panel with a <floatingText> element according to the guidelines in [our editorial decisions document](https://docs.google.com/document/d/1qVETW1qeX1PRrFgswQY8uTrkPC8nWq9YIF2q99dvDj4/edit#heading=h.yl9jpai2cm2n).

##### Transitions
12\. <cbml:panel> (lines 91, 96, and 101): For each panel except for the first, label the transition according to McCloud's definitions by setting the value of `@ana` to the `tr-name` from the [taxonomy](https://github.com/briancroxall/peanuts-taxonomy/blob/master/peanuts-taxonomy.xml). Refer to the [editorial decisions document](https://docs.google.com/document/d/1qVETW1qeX1PRrFgswQY8uTrkPC8nWq9YIF2q99dvDj4/edit#heading=h.yueltgaen2ee) for specific rules that we have adopted for making these decisions. If you are uncertain about a transition, bring it to class and we will discuss it together.

##### Signature and Date
13\. Look for Schulz's signature and date and move the <docAuthor> and <docDate> elements (in panel 4 of the template) to the proper panel. If Schulz writes his name differently, update it in <docAuthor>. If he renders it in a different font or style, encode this with <hi rend="[description]"> using the guidlines from our [editorial decisions document](https://docs.google.com/document/d/1qVETW1qeX1PRrFgswQY8uTrkPC8nWq9YIF2q99dvDj4/edit#heading=h.f6y46wkxdiom). For the date, write it _exactly as Schulz does_ (e.g., `1-15` or `1/15`).

##### Anything Else
We will collectively decide if there's anything else we would like to tag in the strips and how we will do this. We should not let ourselves be governed by the narrow-mindedness of the 2020, 2021, or 2022 classes and their boneheaded professor!



## Credits
I designed the [first version of this assignment in 2018](https://briancroxall.net/w18dh/assignments/tei-edition/) after discussions with [Elli Mylonas](https://library.brown.edu/create/cds/people/elli-mylonas/), TEI aficionado and colleague extraordinaire, and I made some important revisions [in 2019](https://briancroxall.net/w19dh/assignments/tei-markup/). It was updated considerably [in 2020](https://briancroxall.net/w20dh/assignments/encoding-peanuts-with-tei-cbml/) for _Peanuts_, drawing particularly on the work of [John A. Walsh](https://info.sice.indiana.edu/~jawalsh/) and his [Comic Book Markup Language](http://dcl.ils.indiana.edu/cbml/). Working from [Walsh's article in _Digital Humanities Quarterly_](http://www.digitalhumanities.org/dhq/vol/6/1/000117/000117.html), Elli created the basic strip template and taxonomy, and she has helped me refine it further. In 2021, 2022, and 2023, I made a number of updates based on how what we have learned, trying—believe it or not—to make this all easier to understand. A big thanks go to Ashlin Holbrook for re-formatting and organizing the editorial guidelines into a more usable form!
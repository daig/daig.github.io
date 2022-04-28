This is how I use Obsidian, in a way that I think cuts to the core of knowledge organization. May it be useful brain-food for you 🙏

# Nodes vs Edges
Every note has a type, and each type has a toplevel folder containing all notes of that type.
The primary type of a note distinguishes its [[API]] / template.
## Nouns
In the simplest case every "noun" contains its definition - this toplevel type is "node".
More specialized noun types have mandatory fields, stored as [[obsidian template]]s.
Fields are of the form `myField::` for compatibility with [[dataview]] while still working with backlinks, unlike [[yaml]] headers.
Conceptually, such specialized types are [[structural subtypes]], but there's no way to do that currently in [[obsidian]] so in practice there's only the untyped "node" and toplevel specialized types.

Noun types contain _only_ their definition. Properties, notes, and other relationships are handled exclusively by "edges".

## Edges
All relationships between nouns are included in edges (in a toplevel "edges" folder).
Edges are untyped, there's just the toplevel "edges" folder.
Edges contain prose and other relationships between nouns, with the relationship being codified simply by including the nouns as links naturally in the prose.
For example:
```
[[Alice]] recommended [[Bob]] read [[GEB]]
```
or
```
[[Black Garlic]] is #sweet and #savory
```
There's no limit to the amount of nouns connected by an edge, but each edge file should representa a single relationship or (merely as sugar for brevity) simple conjunction of same-type relationships (as the garlic example).

Conceptually, edges are the arrows in a [[closed categoy]] / [[polycategory]], but the proper [[type]] system for that is an open research problem.

## Adjectives
Adjectives are represented as [[obsidian tag]]. They're conceptually used similarly to nouns, but they only appear in edges without a backing file. Their meaning is [[synthetic]]ally infered from how they're linked, and external common-knowledge definition in natural language.
Adjectives should conceptually be on the same footing as nouns (and edges) but [[obsidian]] doesn't treat tags as first-class, yet their features (nesting, tag pane, etc.) are more practical for this usage.

## Notes
Freeform notes are just edges (going in the "edge" folder) with extra timestamp metadata (eg `YYYY-MM-DDH.mm.ss - NAME`) , using the [[obsidian zettelkasten]] format with a simple hotkey (eg `ctrl+shift+z`).

In practice most edges are created this way for minimum friction. They can start as a mere timestamp and get a descriptive name appended later. 

## Navigation
The primary entry points for navigation:

### Nouns
Remembering a specific noun and jumping to it via search / link is the most direct way to navigate.

### Adjectives
Enumerated on the tag pane or searched directly. Adjectives provide fine-grained intersection/union based search for structured concepts spanning multiple nouns - adjectives primarily link into edges, but they are more reliable as entry points than remembering specific edges due to the specialized high-context nature of edges.

### Edges
Edges are in most cases _not_ meant to be accessed directly, hence their default timestamp name. Rather, edges are meant to be used to traverse between nodes with high context. 

#### Backlinks
Adjoin context to nouns and allow discovering other related nouns.

This way, the primary info from the definition is displayed first, as well as on mouse-over, while an open collection of unordered relationships expand below.

#### Graph View
Graph view, and particularly local graph view, are very useful for a big-picture high-context understanding of noun relationships. Ideally, [[obsidian]] would support 2nd-level local graph view to aid noun-edge-noun navigation, but adding descriptive names to edges can dramatically improve the graph-view navigation experience (compared with backlink-based navigation which typically doesn't need descriptive names). For edges which are meant to link many nouns through deep transitive relationships (yet which still resist collecting under a single monolithic edge), strongly consider descriptive names that will help distinguish which edge to traverse in local graph view.

#### Tables

The [[dataview]] plugin is great. It allows collecting structured data into a note for viewing.

### Publishing
[[obsidian publish]] is pretty great. It's a bit pricy for what it is (there's really nothing preventing it from being a static site generator so it's kinda evil to charge such a high subscription imo), but is an extremely low-friction way to open up your brain to the public.

This framework is meant to be published with graph view and search but _without_ file navigation. The idea being that direct entry to edges loses context, as well as some of the mystique of exploring a wide variety of concepts. The main entry point for the casual site-goer will be to get linked to a specific post (edge) (eg via twitter), following only the necessary definitions and graph-visible links - all the best experience of a late-night wikipedia binge. Exposing too many out-of-context files leads to decision fatigue and diffusion of attention, while also exposing potentially spicy content that would normally be soft-walled off from critics by the amount of caringXattention it would take to traverse there.


# Someday~

## Space-Age Types

This framework conceptually matches a crisp typesystem.
[[obsidian]] is great, and able to usably embed the system, but fundamentally lacks some support that would make it seamless.


Proper Fine-Grained typing is the main focus of [[Based]] / [[Liminal]] projects.
Reitterating the desiredatta here:
- Unification of tags, notes, and folders allowing in particular:
	- Subtyping of noun types and flexible heirarchical (folder-like) views as special cases of tag queries
- "Function types" for edges, giving semantic meaning to the difference between (for example) a "person-person" relationship vs a freeform note. What this means practically remains to be discovered, but would allow much better traversal, sophisticated views, and eventually active triggers to allow notes to be used directly as backend protocols (a la [[GraphQL]])
- First-class fields and associated [[row type]]s - allowing better search (eg live [[dataview]]-style queries), semantic templates, and sophisticated type-specific views.

In the long run, these last two features together would allow entire apps to be built on a [[Hasura]]-style model. Eg [[anki]] notes, twitter messages, etc. - with the protocol being first-class & declaratively specified.

Having such a complete type system for protocols would also allow sophisticated sharing and version control functionality.

A lot more to say on these in the future, so don't worry too much about getting this section now - but if it strikes you immediately I'd love to hear from you.

## Publication
Given a strong foundational type system, multiparty protocols become much easier, but a lot of it could be implemented to some extent now:
### Federated collaborative live editing
Collaborative editing (like roam) would be great for [[obsidian]]. Currently, something like [[git]] can be used but it loses the live editing. Something like [[VS Code]] live-share helps here, but the UX leaves a lot to be desired.

Even with [[git]]-based collaborative editing, integrating public and private information is a no-go. Ideally each user would have fine-grained control over view/edit permissions for each note. This can sort of be handled with different bases, but different bases can't link to eachother so it's practically useless as an exo-brain. Hence _Federated_.

### First-Class `dataview`
[[dataview]] is awesome but it doesn't work at all for publish. In practice this means if I want a table of content I have to manually create such a table from the output of a dataview or open up file navigation publically (I explain why I don't want to do this above).

### First-Class tags
Tags "adjectives" are an important organizing principle, but they don't work for [[obsidian publish]] which limits the accessibility of published content. This can be gotten around to some extent by creating currated dataviews for specific tags - but of course those don't work either!

### Backflow
Some way to do comments would elevate published pages to real blog quality. Of course, this is handled automatically by the sophisticated protocol type system & sharing, but comments would be an easy enough feature to tack on directly to the existing obsidian publish given that they're already hosting it directly.


# Conclusion
Hopefully this helps you organize your own thoughts, and inspires _someone_ (👀👀👀) to build better tools!

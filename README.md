The Python Grimoire
===================

<blockquote>
grimoire /grimwaar/ (noun) ::= a book of magic spells and invocations. Origin: French, alteration of grammaire 'grammar'. A grammar is a description of a set of symbols and how to combine them to create well-formed sentences. A grimoire is a description of a set of magical symbols and how to combine them properly. It is sort of a recipe-book for magic spells. See also Grimoire
</blockquote>

The core of the Grimoire was originally developed and released by Andrew M. Kuchling in May, 1999. However, it never reached a stage where Andrew felt that it was ready for publication, and eventually he withdrew it. Steve Ferg, however, had found the Grimoire very helpful as he was learning Python, and he persuaded Andrew to allow him to take over maintenance of the document in August, 2002.

In December 2004, Andrew and Steve released the Grimoire under the Creative Commons Attribution-NonCommercial-ShareAlike License 2.0 and Rui Carmo began hosting it at The Tao of Mac, where it lingered until Rui decided to re-cast it in TiddlyWiki format for ease of use.
Nine years later, it's being (slowly) re-cast as a set of Github pages, in the spirit of the age.

## Contributing

Right now, there's a fair amount of conversion to be done -- most of it trivial, consisting mostly of search/replace.

Just grab [this](http://the.taoofmac.com/media/dev/Python/Grimoire/tiddlygrimoire.html), convert each Wiki item into Markdown and save it as `index.md` into a sensibly named folder under `grimoire` so that we have nice URLs

If you want to contribute new recipes, feel free to do so, but read through some of the existing ones first to get a feel for the way they're written -- I'd rather we stayed close to the spirit of the original text.

As to corrections (like Python 3 changes, etc.), they're most welcome, but keep in mind that the original text was written prior tp Python 2.6 and aimed at beginners.

Which doesn't mean we shouldn't go for advanced topics, or even provide short intros to useful libraries of all kinds.

## Design Credits

This is currently using [Ghink][gk] (and hence the awesome [InK][ink] CSS framework) for layout, which I intend to pare down and tweak for a more documentation-friendly layout. Contributions towards that are also welcome.

  [ink]: http://ink.sapo.pt/ "InK - Interface Kit"
  [gk]: http://ghink.cc/ "Ghink"

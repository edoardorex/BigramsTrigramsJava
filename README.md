# Character N-Gram Counting in Java

Sequential and producer/consumer implementations of a text-corpus analysis
project. The programs count character bigrams and trigrams, generate HTML
frequency tables, and display a graphical execution recap.

## Implementations

| Entry point | Approach |
| --- | --- |
| [src/MainSequential.java](src/MainSequential.java) | Single-process reading, tokenization, and counting |
| [src/it/unifi/Main.java](src/it/unifi/Main.java) | Executor-managed producer and consumer pools |

The concurrent version uses blocking queues, concurrent maps, and atomic
counters. Its current defaults are four producers and two consumers, set in
`Main.main()`.

## Prerequisites and setup

1. Use a Java 8-or-later JDK and a graphical desktop environment.
2. Add compatible **JFreeChart/JCommon** libraries to the project classpath.
   The source imports the legacy `org.jfree.ui.ApplicationFrame` and
   `RefineryUtilities` APIs; current chart-library releases may require source
   changes rather than being drop-in replacements.
3. Set `src` as the source root in your Java IDE.
4. Update `dirName` in **both** entry-point files to your local `Gutenberg/txt`
   directory. The checked-in paths are developer-specific absolute paths.
5. Run `MainSequential` or `it.unifi.Main` using the configured classpath.

No Maven or Gradle build definition is included. The desktop chart and browser
launches mean these entry points are not headless command-line tools.

## Input and output

The sequential implementation splits text into tokens, discards empty tokens
and tokens containing digits, lowercases retained words, and counts character
sequences inside them. Underscore-containing sequences are excluded.

Both entry points print frequency maps and timings. The table generators write
`Bigrams.html` and `Trigrams.html` to the working directory and attempt to open
them in a browser. JFreeChart displays distinct-sequence counts and the most
frequent bigram and trigram.

Historical examples:

![Frequency table](tab.PNG)
![Execution recap chart](graph.PNG)

## Related projects

- [Sequential C version](https://github.com/edoardorex/BigramsTrigramsC).
- [Pthreads C version](https://github.com/edoardorex/BigramsTrigramsPThreads).

These versions use different preprocessing. Control the corpus, runtime, and
input normalization before interpreting performance comparisons.

## Attribution

The original README credits **Edoardo Re, 2020**.
This repository is a fork of
[edoardore/BigramsTrigramsJava](https://github.com/edoardore/BigramsTrigramsJava).
The original source and history remain intact; no license is added or changed.

Contributions should include appropriate tests and explain changes to tokenization
or concurrency. Discuss major changes in an issue first.

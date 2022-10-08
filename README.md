## About
Storage repository for Wiktionary dump file parsed by [JWKTL](https://github.com/dkpro/dkpro-jwktl) and stored in a Berkeley DB. 

## Obtaining Wiktionary data
The first step towards using JWKTL is obtaining the actual Wiktionary data. JWKTL is able to process the XML dump files containing the wiki markup of the Wiktionary articles. These dump files are released by the Wikimedia foundation under a free license. Choose the Wiktionary language edition and data from the download page at http://dumps.wikimedia.org/backup-index.html (e.g., “enwiktionary” for the English Wiktionary) and save the corresponding pages-articles.xml dump (i.e., the dump containing at least “articles, templates, media/file descriptions, and primary meta-pages”) to your hard disk.

The dump file that was parsed to the database provided in this repository can be downloaded from page with [Releases](https://github.com/dpqkdqkj/Wiktionary-database-parsed-by-jwktl/releases).

## Parsing the data
Before JWKTL is ready to use, you need to parse the obtaining Wiktionary dump file. The wiki syntax is being parsed by JWKTL and stored in a Berkeley DB. 

Create a new class and run the parser using the following sample code:
```java
public static void main(String[] args) throws Exception {

    File dumpFile = new File(PATH_TO_DUMP_FILE);
    File outputDirectory = new File(TARGET_DIRECTORY);
    boolean overwriteExisting = OVERWRITE_EXISTING_FILES;
    
    JWKTL.parseWiktionaryDump(dumpFile, outputDirectory, overwriteExisting);
}
```
Make sure to set the following parameters:

- `PATH_TO_DUMP_FILE`: The path to the Wiktionary dump file as downloaded in the preceding step. The dump file can be either an uncompressed XML file (fast) or a bz2 archive of the XML file (a bit slower).
- `TARGET_DIRECTORY`: The name of the output folder, where the parsed Wiktionary database should be placed (needs to be a valid directory).
- `OVERWRITE_EXISTING_FILES`: An existing Wiktionary database in the target directory will only be overwritten if this parameter is set to true.

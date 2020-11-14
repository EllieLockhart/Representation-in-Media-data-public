# Representation-in-Media-data-public
 Part of a project to work towards a better understanding of representation of diverse groups in media. Contains data files designed to create an open-source representation of data related to marginalized groups (currently focused on LGBT+) and their depiction in mass media; it also functions as a repository of popular media, aiming at replacing closed/limited-source sources like the IMDb dataset. 
 
 ## Project Overview
 **Currently, the goal of the project is to compile a reasonably comprehensive of major mass media releases from 1999-2020 and to maintain this list going forward. We want to include all media, including media which is not particularly or at all diverse - this is about creating a base dataset than can be used freely for any purpose, including but certainly not limited to diversity research and software.** The overall project is currently working on developing an app to provide information about LGBT+ representation in titles that fit these criteria; however, we want to create a data set that can stand in as a replacement for other data sets that are commonly used but probably should not be for research and especially public-facing/publicly distributed software. **Due to the sensitivity of this data, we unfortunately have to confirm the intentions of those seeking to join. If you do not know the project administrator, please contact her if you are interested - contributions are welcome, but forces hostile to our project are unfortunately common in the current climate.**

## Methodological Justification
 Doing data science research or, especially, building apps related to entertainment media statistics/recommendations is impaired for low-budget and non-commercial developers and data researchers as a result of the restrictive commercial licenses imposed on commonly available data sets from the most common sources of data on movies, television and video games. Sites like IMDb and Rotten Tomatoes heavily restrict the terms under which their lists of movies, television, and video games may be used - their use for data science is probably an edge case, but it certainly wouldn't be possible to make an app/website which disseminates and/or collects information publicly about this media, even if its use case is largely completely distinct from the original sites. 
 
 For the aforementioned reason, it is essentially necessary to replicate this data manually - while web scraping or even accessing the public datasets of sites like IMDb (which are, again, provided under *very* restrictive licensing terms) is possible, it is not only something which has the potential to lead to legal complications which could destroy the entire project, it is also not helpful to future creators who want to build on open information. While a standard open source license (currently the MIT License, but we are discussing as a group whether slightly more or slightly less restrictivel icense would be appropriate) will be applied to the software we develop with this dataset, the knowledge we seek to gain should be free. Academics, hobbyists, and businesses alike who work with either entertainment *or* diversity will be able to benefit from this dataset in various ways.

 ## Specific Data Goals
 The specific project which has spawned this subproject is the creation of a website/app which provides information on the extent to which LGBT+ people are represented in a given media project; a data science subproject to study the commercial and social significance of including, excluding, or ignoring LGBT+ people in mass media will also be conducted. However, there are several steps that are necessary before any substantial progress can be made toward anything more than a mockup app/website, and these steps require a dataset which will be kept completely open source for use for any purpose.
 
 At this time, the Representation in Media Project's data goals are at the first phase.

 ### Phases of Data Creation
 1. Using the CSV format (which is editable in any common spreadsheet editors, many IDEs, and any text editor), we will assemble a list of as many of the television, video games, and movies that released between January 1, 1999 and today. At least for the time being, new releases will be added on a rolling basis, although this may later be supplanted by a different data insertion method. Again, **the purpose of this data collection is not yet to determine anything about diversity and inclusion**. We want to include everything, from *SimCity* and Pixar's *Up* to *Queer as Folk* and *The Last of Us Part II*.
 2. We will expand the information contained in these files to include basic information related to diversity and inclusion, based on measures to be established by the team.
 3. The files will be exported to a graph database, most likely ONGDB (the open source fork of Neo4J) for querying by apps and for sophisticated data analysis.

 Once we have completed stage three, we will reexamine the "subproject" status of the data gathering, but it will likely continue, with contributors helping to "path" and rebuild the database with .csv edits.
 
 ## How to contribute/code of conduct
 In order to operate legally without infringing on any licenses, even manually copying from sites like IMDb cannot be the *modus operandi*, and the code of conduct of the project forbids this. Essentially this is a project to crowdsource information about movies, television, and video games, and the first thing we want is simply affirmation of the media's existence. That is to say, *Star Wars: Episode VIII: The Last Jedi* is a film released since 1999 and at minimum we want the film's title in a csv file for the appropriate time period and medium (film). At this time, we are not prioritizing (or deprioritizing) media based on the extent to which LGBT+ characters or themes are involved. 

 Anyone should contribute if you search through the .csvs and find a particular item which should be included is not included. In other words, if you know a few movies we haven't included, please open a pull request if you're not part of the project and patch our CSVs. Again, please do not just copy information from sites like IMDb - use your own knowledge, news articles, press releases, information (like date, director, studio, publisher) present in or on metadata of copies you own, etc. **Please do not use any form of data scraping to contribute to this project.** Finally, **don't worry too much about making a mistake** - the goal is to crowdsource data, which we can cure at a later time. These guidelines serve as our code of conduct for purposes of data collection and organizing. Please also review (https://libguides.library.kent.edu/data-management/copyright)[Kent University's research data page] for some context and additional issues to keep in mind.

 What information we ideally want differs depending on the three mediums in the scope of the project - films, video games, and television shows. The schema we are requesting is specified in the following sections:

### General Formatting
In an ideal world where we weren't dependent on git and on reviewing each other's commits, we would directly input all of this data into a graph/document database, or at least use a more sophisticated document-based datastore, such as Microsoft Excel or Google Docs. The intermediate solution we have found is the YAML markup language format. YAML works in the following general structure:

{
    aMovieOrVideoGameOrTvShow
        titles: 
            - A Movie or Video Game or TV Show
            - Another Title for This Thing
        release_date: 2008-07-21 # you can use comments at the end of lines or on their own line with the hash symbol
}

Each type of media has its own specific format; you should review the files and follow the example of the first item. If you aren't sure how to handle something, just add the item and note in a comment that it's ambiguous. 

One policy: even if you have to leave it blank, please include all the fields we are currently collecting even if you don't know all of it. For instance, if you don't know the director or all of the actors, just put the field and leave it blank or include what you can; if it's incomplete and you know that, please do note that with a # comment. If your syntax is problematic, that's fine; as long as it generally resembles the structure, the project adminsitrator will clean it up so that it can be parsed.

Some specific notes for contributors about each type of media:

**General**
- most fields are treated as lists, even if there is only one. Title is the one where this probably seems weirdest; however, there are media that have been *completely* renamed or who have original non-English titles
  - If there's just one title, just put titles:, a carriage return, and an indented "- the correct title." 
  - You don't need to worry about if the title was, say, released both with and without a colon; but if it was released under two totally different titles (for instance, *The Edge of Tomorrow*/*Live/Die/Repeat*), then include those titles on separate indented lines
  - if the original title is not in English, include the non-English original first unless you don't know it. For instance, the 2009 Swedish movie released in English markets as *The Girl with the Dragon Tattoo* should be the second title for that movie, with the first one being *Män som hatar kvinnor*. 
  - Also related to that: if there are multiple films that share a title, this is not a problem at all for the title since we treat that as a list (the version of *Dragon Tattoo* starring Daniel Craig was initially released in English and so the English title would be first anyway).
  - However, every entry for a media item in YAML has to have a no-spaces identifier that has to be unique.
    - We won't be including the 1969 John Wayne film *True Grit* in this data set, since it's from 1969 and we stop 30 years later than that. However, I would still suggest marking the 2010 remake by the Coens with the year in this identifier, just in case we do in the future decide to include older titles.
    - We use camelCase for identifiers, so the unique identifier for the 2010 True Grit would be trueGrit2010.


**Film**
- We only track the original release date, so that's a single date field. The box office grosses are also single items, as is initial release format (only applies for movies).
- initialReleaseFormat should be "theatrical," "streaming," or "home video". (I don't expect, given that we're looking for *major* titles, that we will be including many "home video" releases, especially since "streaming" essentially replaces home video for anything contemporary, such as Disney's 2020 *Mulan*.)
- Again, it's not important at this stage to list all of the actors or to know the distributor, etc. - as with all of these categories, we really want to make sure we have all of the *names* and *release dates*.

**Games**
 - mostly follow the same format, with the caveat that "major creatives" are listed since directors are not present on every game


# XAnime
Easily browse and watch Anime through your Command Line.

## How to use
If you want to use this in your Project, copy all Classes in ``Tools/`` and paste them.
Code Snippets can be found below.

A Tutorial for personal use is coming soon.

### Supported Sites
- [4anime.to](4anime.to)

Please feel free to submit more Sites by opening an [Issue](https://github.com/angelsflyinhell/XAnime/issues/new).
Otherwise, it's fairly easy to add more Sites yourself. If you do so, please open a [Pull Request](https://github.com/angelsflyinhell/XAnime/pulls).


# Code Snippets and Documentation
## Documentation

### search()
```java
  FourAnime.search(String anime);
  
  /*returns: List<String>
        Returns a List of URLs to all Titles available from the search.
          anime   = Name of a Series or Anime.
  */
```

### getTitle()
```java
  FourAnime.getTitle(List<String> urls, int title);
  
  /*returns: List<String>
        Returns a List of URLs to all Episodes available.
          urls    = List of URLs. Best practice is getting this List with search().
          title   = Index of List urls.
  */
```
### getEpisode()
```java
  FourAnime.getEpisode(List<String> urls, int episode);
  
  /*returns: String
        Returns a String with the URL of a specific episode.
          urls       = List of URLs. Best practice is getting this List with getTitle().
          episodes   = Index of List urls.
  */
```

### getVideoURL()
```java
  FourAnime.getVideoURL(String url);
  
  /*returns: String
        Returns a String with the Video URL of a specific episode.
          url   = URL of Episode. Best practice is getting this List with Episode().
  */
```

### getVideoURLWithClass()
```java
  FourAnime.getVideoURL(String url, String htmlClass);
  
  /*returns: String
        Returns a String with the Video URL of a specific episode.
          url       = URL of Episode. Best practice is getting this List with Episode().
          htmlClass = Class Name for HTML Tag.
  */
```

### getAnime()

```java
  FourAnime.getAnime(String anime, int title, int episode);
  
  /*returns: String
        Returns a String with the Video URL of a specific episode.
          anime   = Name of a Series or Anime.
          title   = Selects one of the Search Results for String anime.
          episode = Number of the Episode.
  */
```

## Code Snippets
### Full Request with Input
```java
  public static void main(String[] args) throws IOException {

        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        System.out.println("Specify an Anime:");
        String s = br.readLine();

        List<String> titles = FourAnime.search(s);
        for (int i = 0; i < titles.size(); i++) {
            System.out.println(i + "    |   " + titles.get(i));
        }

        System.out.println("Select a title by typing one of the available numbers:");
        s = br.readLine();

        List<String> episodes = FourAnime.getTitle(titles, Integer.parseInt(s));
        for (int i = 0; i < episodes.size(); i++) {
            System.out.println(i + "    |   " + episodes.get((episodes.size() - i) - 1));
        }

        System.out.println("Select an episode by typing one of the available numbers:");
        s = br.readLine();

        String url = FourAnime.getEpisode(episodes, Integer.parseInt(s));
        System.out.println("Ready to watch: " + FourAnime.getVideoURL(url));
    }
```
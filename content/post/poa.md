+++
authors = []
date = 2020-01-09T23:00:00Z
excerpt = "kj"
hero = "/images/pexels-photo-3617531.jpeg"
timeToRead = 6
title = "poa"

+++
### [Upload Directory](https://forestry.io/docs/editing/media-library/#upload-directory)

The directory where media uploads should be saved, relative to the root of your repository.

### [Public Path](https://forestry.io/docs/editing/media-library/#public-path)

The _URL path_ that maps to your upload directory. For example, a Hugo website might use `static/uploads` as the **upload directory**, and `/uploads` as the **public path** since Hugo copies files placed in `static` directly into the root of the published website.

### [File Path](https://forestry.io/docs/editing/media-library/#file-path)

This value will be appended to both your **upload directory** and **public path**. You can use this setting to specify a subfolder to place your uploads in. You may use the following variables as a way of bucketing your uploads:

* `:year:`: the current year, formatted `YYYY`
* `:month:`: the current month, formatted `MM`
* `:day:`: the current day, formatted `DD`

### [Front Matter Path](https://forestry.io/docs/editing/media-library/#front-matter-path)

You may optionally use a different _public path_ for images uploaded to front matter, as opposed to images uploaded via the content editor. You may wish to do this if you already have the _public path_ value written into your templates where the front matter is used.

## [Furt](https://forestry.io/docs/editing/media-library/#further-reading)
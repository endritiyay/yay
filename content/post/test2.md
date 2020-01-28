+++
authors = []
date = 2020-01-14T23:00:00Z
draft = true
excerpt = "hehehhehe"
hero = "/images/auto_1doc_filmiqendresaA1511767337.jpg"
timeToRead = 6
title = "test2"

+++
### [Use _srcset_ to Deliver Responsive Images](https://forestry.io/blog/master-image-delivery-with-cloudinary/#use-srcset-to-deliver-responsive-images)

The next thing we want to do is provide scaled-down images at smaller resolutions. We can do that using the `srcset` image attribute. `srcset` works by specifying a set of images and leaving it up to the browser to download the appropriately-sized one. This is an easy way to serve smaller images on smaller devices that wouldn’t be able to display the full resolution, and also for ensuring that computers with High-DPI displays can access high-resolution images.

To keep our code organized, I’ve decided to move these responsive image tags into partials. For the image in the single template (`layouts/products/single.html`,) I’ve created a partial at `layouts/partials/images/single-product.html`. We will call this partial in our single template and pass it the image, and also grab our base URL from the site settings:

    <div class="product__image column is-half">
            {{ partial "images/single-product" (dict "image" . "baseURL" $.Site.Params.cloudinary_base_url) }}
    </div>

In our partial, I’ve specified four image sizes for different screens:

    <img 
    srcset="
    {{ .baseURL }}/w_500{{ .image }} 500w,
    {{ .baseURL }}/w_710{{ .image }} 710w,
    {{ .baseURL }}/w_1000{{ .image }} 1000w,
    {{ .baseURL }}/w_1420{{ .image }} 1420w"
    src="{{ .baseURL }}/w_500{{ .image }}"
        />

Browsers that don’t support `srcset` will fall back to the 500px version specified in the `src` tag.

That’s all it takes to add responsive images with Cloudinary!

### [Crop Images For Beautiful Grids](https://forestry.io/blog/master-image-delivery-with-cloudinary/#crop-images-for-beautiful-grids)

Cloudinary’s image transformations give us the ability to do more than just scale images down, however. Similar to what we did with the cart image, we can crop images to fit them to a certain aspect ratio.

Our product list view uses a flexbox-based grid. Effort was made to keep our grid lines strong, but there is room for improvement here. The images used in our product grid have different **aspect ratios**, so when they are resized to the same width, they end up with different heights.
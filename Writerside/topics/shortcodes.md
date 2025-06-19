# Shortcodes


**Devhub shortcodes (NOT entire list, just the ones found so far).**

> **Not an Official List**
>
> - These are shortcodes/macros that were either given to us or we found during implementations & development.
> - MORE can be found as we continue to implement and develop new pages.
>
{style="warning"}

### Image linking in devhub
**Description:**
This section provides a method to link images in the DevHub site using Twig syntax, ensuring that images can be dynamically linked to their respective pages or sections via cloud.


**Example:**
`src="${asset_url_prefix}/img/upload/img_9262-1.jpg"`

**Useage**
```html
${asset_url_prefix}
```

### Phone Link
**Description:**
This section provides a short code for creating a phone link that can be used in HTML editors.

````html
<a href="tel:${phone}">${phone}</a>
````

### MISC Shortcodes

| Shortcode / Macro                  | Value                                                         | Description                                      |
|------------------------------------|---------------------------------------------------------------|--------------------------------------------------|
| `${city}`                          | North Vancouver                                               | City                                             |
| `${state}`                         | BC                                                            | Province/State abbreviation                      |
| `${state_name}`                    | British Columbia                                              | Province/State full name                         |
| `${country}`                       | CA                                                            | Country abbreviation                             |
| `${country_name}`                  | Canada                                                        | Country full name                                |
| `${postal_code}`                   | V7M 2J5                                                       | Postal code                                      |
| `${location_name}`                 | Floor Coverings International of Northshore Vancouver, BC, CANADA | Full location name                               |
| `${custom_location_display_name}`  | Northshore Vancouver BC CANADA                                | Custom display name for the location             |
| `${business_name}`                 | Floor Coverings International                                 | Business name                                    |
| `${site_id}`                       | 1986394                                                       | Site ID                                          |
| `${facebook_url}`                  | https://www.facebook.com/flooringnorthshore/                  | Facebook page URL                                |
| `${instagram_url}`                 | https://www.instagram.com/fcinorthshore/                      | Instagram page URL                               |


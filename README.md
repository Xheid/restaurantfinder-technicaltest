# europages-coding-challenge

## Summary

A developer has just made a POC for our new restaurant application.  
Alas, he's called on a new mission!

You're the one to finish the job.  
It was almost done, but there is some TODO in the code that need do be fixed.

This should be a 1-2 hour exercise.

1. Make a new repo and push your code in it.
2. Make the commit as much atomic as possible.
3. Resolve & remove all TODO from the code (even the `<VAlert>` component)

- begin with the one labelled as MAJOR
- then if you have time proceed to MINOR
- then if you still have time do the PATCH
- …and finish the Bonus if you're are in fury mode!

4. When done, share your updated repository with us!

## Run the application

```bash
# install the dependencies
$ yarn

# serve with hot reload at localhost:3000 (may change the port if already in use)
$ yarn dev:nuxt

# serve the API at localhost:3666
$ yarn dev:api
```

## If you don't know VueJS

VueJS comes with a [solid documentation](https://vuejs.org/)  
You might be very interested in [computed properties](https://vuejs.org/v2/guide/computed.html#Computed-Properties): it's a way to have derived data from your original one.

### tools

- [VueJS devtools](https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd?hl=en) can come very handy.

## Other documentation

### Used libraries

| name               | doc                                            |
| ------------------ | ---------------------------------------------- |
| Vue 2              | https://vuejs.org/                             |
| Nuxt               | https://nuxtjs.org/                            |
| Vuetify            | https://vuetifyjs.com/en/                      |
| Phosphor Icons     | https://phosphoricons.com/                     |
| Phosphor Icons Vue | https://github.com/phosphor-icons/phosphor-vue |

### API Endpoints

|     | URL                                 | Resources     |
| --- | ----------------------------------- | ------------- |
| GET | http://localhost:3666/companies     | all companies |
| GET | http://localhost:3666/companies/:id | 1 company     |

#### A company

```json
{
  "name": "Burgerlich",
  "id": "to7wdG3gaLjTuykEbpB8qg",
  "url": "https://www.yelp.com/biz/burgerlich-hamburg-4?adjust_creative=nMAD8ywU1QBl_RMSM215Bg&utm_campaign=yelp_api_v3&utm_medium=api_v3_graphql&utm_source=nMAD8ywU1QBl_RMSM215Bg",
  "phone": "+494033441852",
  "display_phone": "+49 40 33441852",
  "photos": [
    "https://s3-media3.fl.yelpcdn.com/bphoto/g87Q_elyu0-J-R8NGaHSAA/o.jpg"
  ],
  "location": {
    "address1": "Gänsemarkt 43",
    "city": "Hamburg",
    "postal_code": "20354",
    "formatted_address": "Gänsemarkt 43\n20354 Hamburg\nGermany"
  },
  "reviews": [
    {
      "text": "Just opened location and I'm a big fan. The way the restaurant operates is that there an ipad menus inside every table. You order directly from your table...",
      "rating": 5,
      "id": "to7wdG3gaLjTuykEbpB8qg-0"
    }
    // …
  ]
}
```

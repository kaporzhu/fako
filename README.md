### Fako

[![Circle CI](https://circleci.com/gh/wawandco/fako.svg?style=svg)](https://circleci.com/gh/wawandco/fako) [![Circle CI](https://img.shields.io/badge/godoc-docs-blue.svg)](https://godoc.org/github.com/wawandco/fako)


**Fako** is a library intended to fake Golang structs with fake but coherent data, **Fako** maps struct field tags and generates fake data accordingly.

We find it useful when writing specs to generate fake database data, hope you too.

#### Example

This is an example of how **Fako** works.

```go
import(
  "fmt"
  "github.com/wawandco/fako"
)

type User struct {
    Name     string `fako:"full_name"`
  	Username string `fako:"username"`
  	Email    string `fako:"email_address"`//Notice the fako:"email_address" tag
  	Phone    string `fako:"phone"`
  	Password string `fako:"simple_password"`
  	Address  string `fako:"street_address"`
}

func main(){
  var user User
  fako.Fill(&user)

  fmt.Println(&user.Email)
  // This prints something like AnthonyMeyer@Twimbo.biz
  // or another valid email

  var userWithoutEmail User
  fako.FillOnly(&userWithoutEmail, "Email")
  //This will fill all only the email

  var userWithoutEmail User
  fako.FillExcept(&user, "Email")
  //This will fill all the fields except the email

}
```

Fako provides 3 built in functions `Fill`, `FillOnly`, and `FillExcept`, please go to [godoc](https://godoc.org/github.com/wawandco/fako) for details.

**Fako** support most of the fields on the [fake](https://github.com/icrowley/fake)  library, below you can see a list of the field types you can use.

- brand
- character
- characters
- city
- color
- company
- continent
- country
- credit_card_type
- currency
- currency_code
- digits
- domain_name
- domain_zone
- email_address
- email_body
- email_subject
- female_first_name
- female_full_name
- female_full_name_with_prefix
- female_full_name_with_suffix
- female_last_name
- female_patronymic
- first_name
- full_name
- full_name_with_prefix
- full_name_with_suffix
- gender
- gender_abbrev
- hex_color
- hex_color_short
- ip_v4
- industry
- job_title
- language
- last_name
- latitude_direction
- longitude_direction
- male_first_name
- male_full_name
- male_full_name_with_prefix
- male_full_name_with_suffix
- male_last_name
- male_patronymic
- model
- month
- month_short
- paragraph
- paragraphs
- patronymic
- phone
- product
- product_name
- sentence
- sentences
- simple_password
- state
- state_abbrev
- street
- street_address
- title
- top_level_domain
- user_name
- week_day
- week_day_short
- word
- words
- zip

#### TODO
Allow user to register custom data generators with functions.

#### Credits
As you may have notices this is based on [fake](https://github.com/icrowley/fake) library, which does all the work to generate data.

#### Copyright
Fako is Copyright © 2008-2015 Wawandco SAS. It is free software, and may be redistributed under the terms specified in the LICENSE file.

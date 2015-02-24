# ActiveAdmin::Globalize

Makes it easy to translate your resource fields. Forked from (Stefano Verna)[https://github.com/stefanoverna]'s original repository with some patches applied to support latest ActiveAdmin and Globalize versions.


## Installation

```ruby
gem "activeadmin-globalize", github: 'noematics/activeadmin-globalize'
```

We still need to use GitHub because ActiveAdmin is still in active development
and there's no released gem compatible with Rails 4.

## Your model

```ruby
active_admin_translates :title, :description do
  validates_presence_of :title
end
```

## Editor configuration

```ruby
# if you are using Rails 4 or Strong Parameters:
permit_params translations_attributes: [:locale, :title, :content]


index do
  # ...
  translation_status
  # ...
  default_actions
end

form do |f|
  # ...
  f.translated_inputs "Translated fields", switch_locale: false do |t|
    t.input :title
    t.input :content
  end
  # ...
end
```

If `switch_locale` is set, each tab will be rendered switching locale.

## Friendly ID

If you want to use Friendly ID together with Globalize, please take a look
at the `(friendly_id-globalize)[https://github.com/norman/friendly_id-globalize]` gem.

## Hints

To use the dashed locale keys as `'pt-BR'` or `'pt-PT'` you need to convert a string to symbol (in `application.rb`)

```ruby
config.i18n.available_locales = [:en, :it, :de, :es, :"pt-BR"]
```

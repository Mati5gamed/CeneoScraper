# CeneoScraper

## Kod produktu o którym będą pobierane opinie
84514582

## Algorytm pobierania opini o pojedynczym produkcie z serwisu Ceneo.pl
1. wysłanie rządania dostępu do strony z opiniami o produkcie

2. Jeżeli operacja zakończy się sukicesem, wyodrębnienie z kodu strony fragmentów odpowiadająch poszczególnym opiniom
3. Dla każdej z wyodrębnionych opini wydobycie z kodu HTML poszczególnych składowych i zapisanie ich w postaci złożonych struktur danych.
4. Jeżeli istanieje kolejna strona z opiniami, przejście na tą stronę i powtórzenie kroków 1-4
5. Zapisanie wszystkich opini w bazie danych
## Struktura opini w serwisie Ceneo.pl

|składowa | zmienna| selector|
|---------|--------|---------|
|opinia|review|.js_product-review|
| identyfikator opinii|review_id|['data-entry-id']|
| autora|author|user-post_author-name|
| rekomendację|recomendation|.user-post-author-recomandation > em |
| liczbę gwiazdek|stars|.user-post_score-count|
| treść opinii|contetnt|.user-post_text|
| listę zalet|pros|review-feature__item review-feature__item--positive|
| listę wad|cons|review-feature__item review-feature__item--negative|
| ile osób uznało opinię za przydatną|likes|.vote-yes['data-total-vote']|
| ile osób uznało opinię za nieprzydatną|dislikes|.vote-no['data-total-vote']|
| data wystawienia opinii|publish_date|.user-post__published > time:nth-child(1)['datetime]|
| data zakupu produktu|purchase_date|.user-post__published > time:nth-child(2)['datetime]|
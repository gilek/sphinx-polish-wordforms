# sphinx-polish-wordforms
[Polski język trudna język](http://www.wykop.pl/wpis/10268188/polska-pierogi-polskajezyktrudnajezyk-reddit-moj-j/). Na obecną chwilę [Sphinx](http://sphinxsearch.com/) (wersja 2.2.9) nie oferuje żadnego lematyzatora oraz stemmera dla języka polskiego. Sytuacja pewnie szybko się nie zmieni, zatem jesteśmy zmuszeni korzystać z pliku wordforms.

Słownik stworzony został w oparciu o plik [sjp-odm-20141029.zip](http://sjp.pl/slownik/odmiany/). Pomysł na jego wykorzystanie zaczerpnąłem z [bloga allegro](http://blog.allegrogroup.com/it/jak-wygenerowac-dobry-plik-wordforms-dla-silnika-wyszukiwania-sphinx).

Plik zawiera wyrazy o długości przynajmniej 2 znaków. Nieistotna jest wielkość liter, a znaki diakrytyczne są usuwane. Ignorowane są również znaki:  {-,－, ., '}.

Konfiguracja indeksu powinna wyglądnąć z następujący sposób:
<pre>
charset_table 	= 0..9, A..Z->a..z, a..z, \
	U+104->a, U+106->c, U+118->e, U+141->l, U+143->n, \
	U+0D3->o, U+15A->s, U+179->z, U+17B->z, U+105->a, \
	U+107->c, U+119->e, U+142->l, U+144->n, U+0F3->o, \
	U+15B->s, U+17A->z, U+17C->z, \
	U+00E9->e, U+00FC->u
min_word_len	= 2
ignore_chars	= U+002D, U+FF0D, U+002E, U+0027
</pre>

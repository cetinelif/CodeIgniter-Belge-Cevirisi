################
CodeIgniter URLs
################

URL CodeIngiter'da arama-motoru ve kullan�c� dostu varsay�larak tasarlanm��t�r. Standart "sorgu dizisi" (query string) yakla��m� yerine, dinamik sistemli e� anlaml�, CodeIgniter **par�a-tabanl�** yakla��m�n� kullan�r::

	example.com/news/article/my_article

.. not::  Sorgu dizisi URL opsiyon olarak a�a��da tan�mland��� gibi kullan�labilir.

URI Par�alar�
============

Model-View-Controller yakla��m�nda URL par�alar� genelde ��yle sunulur::

	example.com/class/function/ID


#. �lk par�a controller **s�n�f�n�** hat�rlat�r.
#. �kinci par�a s�n�ftaki **fonksiyon** ya da metodu �a��r�r.
#. ���nc� par�a ya da di�er ek par�alar, ID ile g�sterilir ve controller'a de�i�ken olarak g�nderilir.

The :doc:`URI S�n�f� <../libraries/uri>` ve :doc:`URL Helper <../helpers/url_helper>` dosyalar�, URI bilgilerini kolayca kullanman�z� sa�layan fonksiyonlara sahiptir. Ek olarak, URL de�eriniz :doc:`URI Y�nlendirme <routing>` �zelli�iyle daha esnek bir �zellik i�in yeniden tan�mlanabilir.

Adresten Index.php kald�rmak
===========================

**index.php** dosyas� a�a��daki URL'de bulundu�unu varsayal�m::

	example.com/index.php/news/article/my_article

Bu dosyay� .htaccess dosyas�nda yazaca��n�z bir ka� basit kural ile kald�rabilirsiniz. Burada verilen �rnek dosya ile, kullan�lan ��kartma  metodu ile her�eyi yeniden y�nlendirebilirsiniz:

::
	
	RewriteEngine on
	RewriteCond $1 !^(index\.php|images|robots\.txt)
	RewriteRule ^(.*)$ /index.php/$1 [L]

Yukar�daki �rnekte, index.php, images ve robots.txt dosyalar�ndan farkl� her HTTP istemi index.php dosyam�z� �a��rm�� i�lemi g�recektir.

URL Soneki Eklemek
===================

**config/config.php** dosyan�zda, istedi�iniz soneki ekleyerek CodeIgniter taraf�ndan URL olu�turulmas�n� tan�mlayabilirsiniz. �rne�in, e�er URL ��yle ise::

	example.com/index.php/products/view/shoes

Se�ti�iniz bir sonek, mesela **.html,** sayfan�z� ��yle g�sterilmesini sa�lar::

	example.com/index.php/products/view/shoes.html

Sorgu Dizisi �mkan�
======================

Baz� durumlarda URL'nizde sorgu dizisi kullanmay� tercih edebilirsiniz::

	index.php?c=products&m=view&id=345

CodeIgniter, **application/config.php** dosyas�yla bu imkan� kullanman�za olanak tan�r. E�er config dosyan�z� a�arsan�z �unlar� g�receksiniz::

	$config['enable_query_strings'] = FALSE;
	$config['controller_trigger'] = 'c';
	$config['function_trigger'] = 'm';

E�er "enable_query_strings" de�erini TRUE olarak de�i�tirirseniz bu �zellik aktif olacakt�r.  Controller ve fonksiyonlar�n�z tetikleyici kelime geldi�inde, ayarlarsan�z controller ve metodlar�n�za ula�abilir::

	index.php?c=controller&m=method

.. Not:: IE�er sorgu dizisi kullanacaksan�z, URL helper (ve URL �reten di�er helper, mesela baz� form helper'� gibi) gibi par�a tabanl� URL'ye uygun tasarlanm�� helper kullanmak yerine, kendi URL'nizi in�a etmelisiniz.

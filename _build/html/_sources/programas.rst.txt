Programas
+++++++++++


SkySafari Plus (Android)
--------------------------

Para buscar estrellas y añadir a lista de observaciones, una de las mejores formas, para las dobles es pasar de RA,DEC a WDS:

::

	Lambda  Ari     01 57.9         +23 36
	-->
	WDS 01579+2336

Buscamos eso en la app (*search*) y lo añadimos.

Tb se podría hacer un programa para pasar de formato excel o texto a skysafari: 

	http://skysafariastronomy.com/support/manual/observing_lists.shtml
	http://www.southernstars.com/support/faq/skysafari.html

	https://pastebin.com/3AxC0pwh
	http://www.astronomo.org/foro/index.php?PHPSESSID=2rq9ildmrr2l6panpab6tltu73&topic=13464.0


Listas:

	http://jareksastro.org/telescopes.htm
	https://stargazerslounge.com/topic/274840-sky-safari-observing-lists/
	http://skygazerlists.com/
	http://skygazerlists.com/pre-defined/


Programa en python para hacer de texto a list:

::

	head = "SkySafariObservingListVersion=3.0"
	begin_obj = "SkyObject=BeginObject\n\tObjectID="
	end_obj = "EndObject=SkyObject"
	catalog = "CatalogNumber="
	line = "\n"
	tab = "\t"
	star = "2,-1,-1"
	solar_system = "1,-1,-1"
	deep_sky = "4,-1,-1"

	list_ss = head + line


	def write_object(obj, type="star"):
	    type_ = type
	    if type_ == "star":
	        type_ = star
	    elif type_ == "solar_system":
	        type_ = solar_system
	    elif type_ == "deep_sky":
	        type_ = deep_sky
	    else:
	        type_ = star

	    txt = begin_obj + type_ + line
	    txt = txt + tab + catalog + obj + line
	    txt = txt + end_obj + line
	    return txt

	oo = "4 Lyr"
	list_ss += write_object(oo, "star")
	print list_ss

	# we will expect a file with object catalog name
	file_ = ""
	with open(file_, 'r') as f:
	            objects = f.read()

	## to be continued....

**En R:**

Ver aqui: https://gist.github.com/miguelvb/1108e145b01527833b893fb207ebcd1a


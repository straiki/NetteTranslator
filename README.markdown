Nette Translator (c) Patrik Votoček (Vrtak-CZ), 2010 (http://patrik.votocek.cz)

Note
----
This is short manual how to use Nette Translator in the newest Nette 2.0 in its most simple version.
No need to edit or operate with .po/.mo files required. Written 2012-02-10.


1. Enable Translator
===

config.neon:

	common:
		parameters:
			langDir = %appDir%/lang # folder with lang files
			variable.lang = cs_CZ # default language

		services:
			translator:
				factory: NetteTranslator\Gettext::getTranslator


2. Add files + register panel
***

bootstrap.php:

	$container->translator->addFile("%appDir%/lang/","main"); // at least one file required
	NetteTranslator\Panel::register($container, $container->translator);


3. Use in templates
----

default.latte:

	{_"Dog"}
	{_"Cat", $number} // for plural, default are Czech plurals: 1, 2-4, 5+


4. Use in forms
----

MyPreseneter.php:	

	createComponentMyForm ()
	{
		$form = new Form;
		// ...

		$form->setTranslator($this->context->translator);
	}
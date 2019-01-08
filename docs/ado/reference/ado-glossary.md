---
title: Glossaire ADO | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ADO, glossary
ms.assetid: b0478836-4123-4357-969a-c5784fc28be5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3b93ee4ab5b57414d8c8d640bc12a5ebbff882c6
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52530387"
---
# <a name="ado-glossary"></a>Glossaire ADO
Cette rubrique définit les termes pertinents se rapportant à ADO.  
  
## <a name="a"></a>A  
 URL absolue  
 URL complète qui spécifie l’emplacement d’une ressource qui se trouve sur Internet ou un intranet. Voir aussi *URL* et *URL relative*.  
  
 Contrôle ActiveX  
 Inscription automatique, dans le processus composant COM qui a souvent un élément visuel au moment du design ou le moment de l’exécution. Contrôles ActiveX ont également la possibilité de communiquer avec un conteneur de documents actifs, tels que Microsoft Internet Explorer.  
  
 ADISAPI (avancé des données Internet Server Application Programming Interface)  
 DLL ISAPI qui fournit l’analyse, le contrôle Automation, le marshaling de jeu d’enregistrements et l’empaquetage MIME. Le composant ADISAPI fonctionne via l’API fournie par les Services Internet (IIS). Voir aussi *ISAPI*.  
  
 fonction d'agrégation  
 Dans une requête, une fonction telle que COUNT ou AVG STDEV qui calcule une valeur à l’aide de toutes les lignes dans une colonne d’une table. Dans l’écriture d’expressions et dans la programmation, vous pouvez utiliser les fonctions d’agrégation SQL (y compris les trois ci-dessus) et les fonctions d’agrégation domaine pour déterminer différentes statistiques.  
  
 alias  
 Un autre nom que vous donnez à une colonne ou une expression dans une instruction SQL SELECT, souvent plus courte ou plus explicite. Par exemple, BobSales est l’alias dans l’instruction SELECT suivante : « Select wr-Sales as BobSales from SalesDB ». Un alias peut être utilisé pour attribuer dynamiquement des colonnes aux liaisons de contrôle sur l’objet DataControl.  
  
 thread cloisonné  
 Modèle dans lequel tous les appels à un objet se produisent sur un thread de thread COM. Dans le modèle de thread cloisonné, COM synchronise et marshale les appels. Voir aussi *COMmddefcom*.  
  
 opération asynchrone  
 Une opération qui retourne le contrôle au programme appelant sans attendre que l’opération se termine. Avant que l’opération soit terminée, l’exécution de code se poursuit. Voir aussi *opération synchrone*.  
  
## <a name="b"></a>B  
 entrée de liaison  
 Un mappage entre un champ dans une table et une variable. Dans les extensions ADO de Visual C++, **Recordset** champs sont mappés à des variables C/C++.  
  
 Masque de bits  
 Une valeur numérique destiné à une comparaison de valeurs de bit par bit avec d’autres valeurs numériques, généralement indiquer les options disponibles dans les paramètres ou valeurs de retour. Cette comparaison est généralement effectuée par des opérateurs logiques au niveau du bit, tels que **et** et **ou** en Visual Basic, **&** et **&#124;** en C++.  
  
 Par exemple, le ADO **FieldAttributeEnum** valeurs peuvent être utilisées comme des masques de bits pour déterminer les attributs d’un champ. Supposons que vous souhaitez déterminer si un champ a été mise à jour. Pour cela, vous pouvez tester avec l’expression suivante dans Visual Basic :`Field.Attributes AND adFldUpdatable`  
  
 Si le résultat est TRUE, le champ est modifiable.  
  
 signet  
 Un marqueur qui identifie de manière unique une ligne dans un ensemble de lignes afin qu’un utilisateur peut y accéder rapidement.  
  
 objet métier  
 Objet qui effectue un ensemble défini d’opérations, telles que la logique de règle de validation ou de business data. Les objets métier résident généralement sur la couche intermédiaire.  
  
 règle d’entreprise  
 La combinaison de modifications de validation, les vérifications d’ouverture de session, les recherches de base de données, stratégies et transformations algorithmiques qui constituent le moyen d’une entreprise de faire des affaires. Également appelé *logique métier*.  
  
## <a name="c"></a>C  
 expression calculée  
 Expression non constante, mais dont la valeur dépend d’autres valeurs. Pour être évaluée, une expression calculée doit obtenir et calculer des valeurs provenant d’autres sources, généralement dans les autres champs ou des lignes.  
  
 Chapitre  
 Une référence à une plage de lignes à partir d’une source de données. Dans ADO, un chapitre est généralement une référence à un autre **Recordset**.  
  
 Colonnes de chapitres rendent possible de définir un *parent-enfant* relation où la *parent* est la **Recordset** contenant la colonne de chapitre et les  *enfant* est la **Recordset** représenté par le chapitre.  
  
 alias du chapitre  
 Un alias qui fait référence à la colonne ajoutée au parent.  
  
 jeu de caractères  
 Un mappage d’un jeu de caractères à leurs valeurs numériques. Par exemple, Unicode est un caractère de 16 bits capable de coder tous les caractères connus et son utilisation comme une norme de codage de caractères dans le monde entier.  
  
 child  
 Le côté dépendant d’une relation hiérarchique. Un enfant est un nœud dans une structure hiérarchique qui possède un autre nœud au-dessus de lui (de plus près à la racine). Voir aussi *enfant-alias*, *relation parent-enfant*, *parent*.  
  
 alias-enfant  
 Un alias qui fait référence à l’enfant. Voir aussi *alias*, *enfant*.  
  
 CLSID (identificateur de classe)  
 Un identificateur unique universel (UUID) qui identifie un composant COM. Chaque composant COM possède son CLSID dans le Registre Windows afin qu’il peut être chargé par d’autres applications. Voir aussi *ProgID*, *COM*.  
  
 couche cliente  
 Une couche de logique d’un système distribué qui présente en général des données et les processus d’entrée à partir de l’utilisateur, parfois appelé le *front-end*. En règle générale, la couche cliente demande des données à partir d’un serveur basé sur l’entrée, puis met en forme et affiche le résultat. Voir aussi *intermédiaire*, *couche de source de données*, *application distribuée*.  
  
 COM (Component Object Model)  
 Norme binaire permettant aux objets d’interagir dans un environnement réseau, quel que soit le langage dans lequel elles ont été développées ou sur les ordinateurs qu’ils résident. Technologies basées sur COM incluent des contrôles ActiveX, l’automatisation et objets liés et incorporés (OLE). COM permet à un objet d’exposer ses fonctionnalités à d’autres composants et d’héberger des applications. Il définit comment l’objet expose lui-même et comment cette exposition fonctionne sur les processus et les réseaux. COM définit également le cycle de vie de l’objet.  
  
 Composant COM  
 Fichier binaire - telles que .dll, .ocx et certains fichiers .exe - qui prend en charge la norme COM pour fournir des objets. Ce fichier contient le code pour un ou plusieurs fabriques de classes, les classes COM, les mécanismes d’entrée de Registre, le code de chargement et ainsi de suite.  
  
 Opérateur de comparaison  
 Un opérateur qui compare deux expressions et retourne une valeur booléenne.  
  
 Un paramètre de critères qui peut-être être exprimé en tant que « > » (supérieur à), »\<» (inférieur à), « = » (égal), « > = » (supérieur ou égal à), « < = » (inférieur ou égal à), « <> » (non égal), ou « like » (critères spéciaux).  
  
 component  
 Objet qui encapsule les données et le code et fournit un ensemble précis de services disponibles publiquement.  
  
 fichier composé  
 Une implémentation de COM structurée de stockage pour les fichiers. Un fichier composé stocke des objets distincts dans un seul fichier structuré, constitué de deux éléments principaux : les objets de stockage et les objets de flux. Ensemble, elles fonctionnent comme un système de fichiers dans un fichier.  
  
 Un nombre de fichiers individuels liés dans un fichier physique. Chaque fichier dans un fichier composé est accessible comme s’il s’agissait d’un seul fichier physique.  
  
 constant  
 Une valeur numérique ou de chaîne qui ne change pas. Les énumérations ADO nommées (constantes énumérées) peuvent être utilisées dans votre code au lieu des valeurs réelles, par exemple, **adUseClient** est une constante dont la valeur est 3. (Const adUseClient = 3). Voir aussi *énumération*.  
  
 cursor  
 Un élément de base de données qui contrôle la navigation entre les enregistrements, mise à jour des données et la visibilité des modifications apportées à la base de données par d’autres utilisateurs.  
  
## <a name="d"></a>D  
 Liaison de données  
 Le processus d’association d’objets ou contrôles d’une application à une source de données. Un contrôle associé à une source de données est appelé un *contrôle lié aux données*.  
  
 Le contenu d’un contrôle lié aux données est associé à des valeurs à partir d’une base de données. Par exemple, un contrôle de grille est lié à un **Recordset** objet peut être mis à jour lorsque les lignes dans le **Recordset** sont mis à jour. Lorsque les nouvelles valeurs sont récupérées par le **Recordset**, nouvelles valeurs sont affichées dans la grille.  
  
 fournisseur de données  
 Logiciel qui expose des données à une application ADO directement ou via un fournisseur de services. Consultez également le fournisseur de services.  
  
 mise en forme des données  
 Une technique qui utilise une syntaxe formalisée (appelée **forme langage**) pour définir spécialisé **Recordset** objet (appelé un *en forme de jeu d’enregistrements*) qui ne contient pas données mais également références à d’autres **Recordset** objets et/ou des valeurs calculées en fonction de ceux des autres **Recordset** objets.  
  
 couche de source de données  
 Une couche de logique d’un système distribué qui représente un ordinateur exécutant un SGBD, par exemple une base de données SQL Server. Voir aussi *couche cliente*, *intermédiaire*, *application distribuée*.  
  
 DCOM  
 Un protocole de communication qui permet aux composants COM communiquer directement entre eux sur un réseau. Voir aussi *COM*, *composant*.  
  
 DDL (Data Definition Language)  
 Instructions SQL qui définissent, par opposition à manipuler des données. Le schéma d’une base de données est créé ou modifié avec le langage DDL. Par exemple, **CREATE TABLE**, **CREATE INDEX**, **GRANT**, et **RÉVOQUER** sont des instructions DDL SQL.  
  
 flux par défaut  
 Un flux de texte ou binaire (représenté par un **Stream** objet) qui est associé **enregistrement** ou **Recordset** objets lors de l’utilisation de certains fournisseurs OLE DB, telles que le Fournisseur Microsoft OLE DB pour la publication Internet. Le flux par défaut contient généralement le contenu d’un fichier, telles que le code HTML pour la racine d’un site Web.  
  
 application distribuée  
 Un programme écrit de sorte que le traitement puisse être partagé entre plusieurs ordinateurs sur un réseau. En règle générale, une application distribuée est divisée en présentation, logique métier et données, magasin de couches, ou *niveaux*. Voir aussi niveau client, niveau intermédiaire, niveau source de données.  
  
 jeu d’enregistrements déconnecté  
 Un **Recordset** objet dans un cache de client qui n’a plus une connexion active au serveur. Si la source de données d’origine doit être accessible à nouveau pour une raison quelconque, telles que la mise à jour des données, la connexion doit être rétablie. Toutefois, les collections, les propriétés et les méthodes d’un déconnecté **Recordset** sont toujours accessibles.  
  
 DML (Data Manipulation Language)  
 Instructions SQL qui manipulent, par opposition à définir des données. Les valeurs dans une base de données sont sélectionnées et modifiés avec DML. Par exemple, **insérer**, **mise à jour**, **supprimer**, et **sélectionnez** sont des instructions DML SQL.  
  
 fournisseur de source de document  
 Une classe spéciale de fournisseurs qui gèrent des dossiers et des documents. Quand un document est représenté par un **enregistrement** objet ou un dossier de documents est représenté par un **Recordset** de l’objet, le fournisseur de source de document remplit ces objets avec un ensemble unique de champs qui décrire les caractéristiques du document, au lieu du document lui-même. Consultez également l’enregistrement de ressource.  
  
 DSN (nom de source de données)  
 La collection d’informations utilisées pour connecter votre application à une base de données ODBC. Le Gestionnaire de pilotes ODBC utilise ces informations pour créer une connexion à la base de données. Une source de données peut être stockée dans un fichier (un fichier DSN) ou dans le Registre Windows (DSN système).  
  
 propriété dynamique  
 Une propriété spécifique à un fournisseur de données ou le service de curseur. Le **propriétés** collection d’un objet est automatiquement renseignée avec ces (« dynamique »). Un objet n’a pas de propriétés dynamiques jusqu'à ce qu’il est connecté à une source de données via un fournisseur de données particulier. Voir également les données fournisseur, le curseur.  
  
## <a name="e"></a>E  
 Énumération  
 Une liste de constantes nommées. Valeurs énumérées ne doivent pas être uniques. Toutefois, le nom de chaque valeur doit être unique dans l’étendue où l’énumération est définie. Dans ADO, les énumérations sont utilisées pour le paramètre numérique et valeurs de retour, pour ajouter la signification vers du code ADO et protègent le développeur à partir des valeurs numériques (qui peuvent changer à partir d’une version à l’autre). Par exemple, pour ouvrir un statique **Recordset**, utilisez le **adOpenStatic** valeur énumérée : `Recordset.Open ,,adOpenStatic`  
  
 Également appelé *constante énumérée*. Voir aussi *constante*.  
  
 événement  
 Une action reconnue par un objet pour lequel vous pouvez écrire du code pour répondre. Événements peuvent être générés par l’exécution de la commande, l’achèvement de la transaction, navigation de jeu d’enregistrements et mises à jour des données, entre autres. Voir aussi *Gestionnaire d’événements*.  
  
 gestionnaire d'événements  
 Un gestionnaire d’événements est le code qui est exécuté lorsqu’un événement se produit. Consultez également l’événement.  
  
## <a name="h"></a>H  
 gestionnaire  
 Une routine qui gère une condition de relativement simple et courant ou d’une opération, telle que la gestion de données ou de récupération des erreurs.  
  
 Recordset hiérarchique  
 Un **Recordset** qui contient une autre **Recordset**. Voir également les données de mise en forme, chapitre.  
  
 Pour plus d’informations, consultez [accès aux lignes d’un Recordset hiérarchique](../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md).  
  
 hiérarchie  
 En règle générale, une hiérarchie est une structure possédant un haut niveau et les niveaux subordonnés. Dans ADO, hiérarchique **Recordsets** sont utilisés pour représenter la relation parent-enfant entre un enregistrement et un chapitre. Également dans ADO, **enregistrement** et **Stream** objets peuvent être utilisés pour accéder à des arborescences hiérarchiques, telles que des documents et un dossier. ADO MD comprend aussi **hiérarchie** objets pour représenter une relation entre les niveaux d’une dimension dans un cube OLAP. Voir aussi Recordsets hiérarchiques, relation parent-enfant, chapitre, arborescence.  
  
## <a name="i-l"></a>J’AI-L  
 ISAPI (Internet Server Application programmation Interface)  
 Un ensemble de fonctions pour les serveurs Internet, tel qu’un serveur de 2000 Windows NT® Server/Windows exécutant Microsoft® Internet Information Services (IIS).  
  
 Touche  
 Une ou plusieurs colonnes dans une table qui identifient de manière unique une ligne ; souvent utilisé pour indexer une table.  
  
## <a name="m"></a>M  
 Marshaling  
 Le processus de création de package, d’envoi et par-delà interface des paramètres de méthode au-delà des limites de thread ou processus.  
  
 Niveau intermédiaire  
 La couche de logique dans un système distribué entre une interface utilisateur ou de client Web et de la base de données. Il s’agit en général dans lequel les objets métier sont instanciés. La couche intermédiaire est une collection de règles d’entreprise et les fonctions qui génèrent et fonctionnent lors de la réception d’informations. Ils y parvenir via des règles d’entreprise, qui peuvent changer fréquemment et par conséquent encapsulées dans des composants qui sont physiquement séparés à partir de la logique d’application. Également appelé *niveau serveur d’applications*. Voir aussi application distribuée, niveau client, niveau source de données.  
  
 MIME (multi-purpose Internet Mail Extension)  
 Protocole Internet développé à l’origine pour permettre l’échange de messages de courrier électronique avec du contenu riche sur un réseau hétérogène, machine et environnements de messagerie. Dans la pratique, MIME a également été adopté et étendu par les applications de messagerie non.  
  
 MIME est une norme qui permet aux données binaires à publier et de lire sur Internet. L’en-tête d’un fichier avec des données binaires contient le type MIME des données. Il informe les programmes clients (navigateurs Web et programmes de messagerie, par exemple) qu’ils doivent gérer les données d’une autre façon qu’elles gèrent le texte de droite. Par exemple, l’en-tête d’un document Web contenant une image JPEG contient le type MIME spécifique au format de fichier JPEG. Ainsi, un navigateur afficher le fichier avec sa visionneuse JPEG, s’il en existe.  
  
## <a name="n-o"></a>N-O  
 node  
 Un élément dans une arborescence hiérarchique. Un nœud peut être la racine, ou l’enfant d’un autre nœud. Un nœud peut également être le parent de plusieurs enfants. Voir aussi hiérarchie, arborescence, racine, enfant, parent.  
  
 variable objet  
 Variable qui contient une référence à un objet. Par exemple, `objCustomObject` est une variable qui pointe vers un objet de type CustomObject :`Set objCustomObject = CreateObject(adodb.Recordset)`  
  
 ODBC (Open Database Connectivity)  
 Language interface de programmation standard utilisée pour se connecter à une variété de sources de données. Cela est généralement accessible via le panneau de configuration, où les noms de source de données (DSN) peuvent être affectés à utiliser des pilotes ODBC spécifiques.  
  
 OLE DB  
 Un ensemble d’interfaces qui exposent des données à partir de diverses sources à l’aide de COM. Interfaces OLE DB fournissent des applications avec accès uniforme aux données stockées dans diverses sources d’informations. Ces interfaces prennent en charge la fonctionnalité SGBD appropriée à la source de données, ce qui lui permet de partager ses données. Voir aussi COM.  
  
 verrouillage optimiste  
 Type de verrouillage dans lequel la page de données contenant un ou plusieurs enregistrements, y compris l’enregistrement en cours de modification, n’est pas disponible à d’autres utilisateurs uniquement pendant que l’enregistrement est mis à jour par le **mise à jour** mais est disponible avant et après le l’appel à **mise à jour**.  
  
 Le verrouillage optimiste est utilisé lorsque le **Recordset** objet est ouvert avec le **LockType** paramètre ou la valeur de propriété **adLockOptimistic** ou  **adLockBatchOptimistic**. Consultez également le verrouillage pessimiste.  
  
 valeur ordinale  
 Emplacement d’un élément dans un ordre numérique. Dans une collection ADO, la valeur ordinale du premier élément est zéro (0). L’élément suivant est un (1) et ainsi de suite.  
  
## <a name="p"></a>P  
 commande paramétrable  
 Une requête ou une commande qui vous permet de définir les valeurs de paramètre avant l’exécution de la commande. Par exemple, une chaîne SQL peut être paramétrée en incorporant des marqueurs de paramètres dans la chaîne SQL (désigné par le « ? » caractères). Ensuite, l’application spécifie les valeurs pour chaque paramètre et exécute la commande.  
  
 parent  
 Le contrôle côté d’une relation hiérarchique. Dans une structure hiérarchique, un parent a un ou plusieurs nœuds enfants juste en dessous dans la hiérarchie. Voir aussi alias-parent, relation parent-enfant, enfant.  
  
 alias du parent  
 Un alias qui fait référence au parent. Voir aussi alias, parent.  
  
 relation parent-enfant  
 Une relation dans une structure hiérarchique dans lequel le parent est un niveau supérieur et directement associé à un ou plusieurs enfants. Un enfant est un niveau inférieur et doit avoir un seul parent. Voir aussi parent, enfant.  
  
 Verrouillage pessimiste  
 Type de verrouillage dans lequel la page contenant un ou plusieurs enregistrements, y compris l’enregistrement en cours de modification, n’est pas disponible à d’autres utilisateurs pour vous assurer qu’une mise à jour sera établie. Comportement de verrouillage pessimiste est défini par le fournisseur OLE DB. En règle générale, les enregistrements sont verrouillés lors de la modification et reste indisponibles jusqu'à ce que le **mise à jour** méthode est terminée.  
  
 Verrouillage pessimiste est activé lorsque la **Recordset** objet est ouvert avec le **LockType** paramètre ou la valeur de propriété **adLockPessimistic**. Consultez également le verrouillage optimiste.  
  
 Le regroupement  
 Optimisation des performances basée sur l’utilisation de collections de ressources alloués au préalable, tels que des objets ou des connexions de base de données. Il est plus efficace pour dessiner une ressource existante à partir du pool que la création d’une nouvelle ressource.  
  
 ProgID (identificateur programmatique)  
 Un nom unique mappé au Registre Windows par une application COM. Le ProgID pour une connexion ADO est « ADODB. Connexion ». Voir aussi CLSID, COM.  
  
 Proxy  
 Un objet spécifique de l’interface qui fournit le marshaling des paramètres et la communication nécessaires à un client pour appeler un objet d’application est en cours d’exécution dans un environnement d’exécution différents, tels que sur un thread différent ou dans un autre processus. Le proxy se trouve avec le client et communique avec un stub correspondant qui se trouve à l’objet d’application qui est appelée. Voir aussi stub.  
  
## <a name="r"></a>R  
 URL relative  
 URL partielle qui spécifie une ressource sur Internet ou sur un intranet dont l’emplacement est relatif à un point de départ spécifié par une URL absolue ou d’un objet connexion ADO équivalent. En effet, le concaténée absolue et relative URL constituer une URL complète. Voir aussi URL et URL absolue.  
  
 source de données distante  
 Une source de données qui existe sur un autre ordinateur, plutôt que sur le système local (où l’application cliente s’exécute).  
  
 enregistrement de ressource  
 Un enregistrement d’un fournisseur de source de document qui contient des champs pour la définition et la description d’un dossier ou un document. Le document lui-même n’est pas contenu dans l’enregistrement de ressource, mais généralement accessibles par le flux par défaut ou un champ dans l’enregistrement de ressource contenant une URL. Voir aussi fournisseur de source de document, URL du flux par défaut.  
  
 ensemble de lignes  
 Un ensemble de lignes à partir d’une source de données, tous ayant le même schéma de champ. Un ensemble de lignes peut représenter tout ou partie des champs d’une table. Un ensemble de lignes peut également représenter une table virtuelle, créée par une requête ou une jointure de deux ou plusieurs tables. Dans ADO, les ensembles de lignes sont représentés par **Recordset** objets.  
  
## <a name="s"></a>S  
 Portée  
 La plage de référence pour un objet ou une variable ou une plage d’enregistrements dans une table ou vue. Par exemple, les variables locales peuvent être référencées uniquement dans la procédure dans laquelle elles ont été définies. Variables publiques sont accessibles à partir de n’importe où dans l’application. Objets, tels que la base de données en cours sont dans la portée si elles se trouvent dans le chemin d’accès de recherche définis. Plages d’enregistrement peuvent être spécifiés avec une clause d’étendue dans de nombreuses commandes.  
  
 fournisseur de services  
 Logiciel qui encapsule un service en production et la consommation des données, étendant les fonctionnalités de vos applications ADO. C’est un fournisseur qui n’expose pas directement les données, au lieu de cela, il fournit un service, telles que le traitement de requête. Le fournisseur de services peut traiter les données fournies par un fournisseur de données. Consultez également le fournisseur de données.  
  
 jeu d’enregistrements mis en forme  
 Un **Recordset** dont les colonnes ont été spécifiquement définies pour contenir des données, mais également références (appelés chapitres) à d’autres **Recordset** objets et/ou des valeurs calculées en fonction des autres **Recordset** objets.  
  
 frère  
 Les deux nœuds ou plus dans une structure hiérarchique qui se trouvent sur le même niveau dans la hiérarchie. Le nœud racine dans une hiérarchie possède aucun frère.  
  
 procédure stockée  
 Collection précompilée du code tel que des instructions SQL et des instructions de flux de contrôle facultatives stockées sous un nom et traitées en tant qu’unité. Procédures stockées sont stockées dans une base de données ; ils peuvent être exécutées avec un appel à partir d’une application et autoriser les variables déclarées par l’utilisateur, l’exécution conditionnelle et autres puissantes fonctionnalités de programmation.  
  
 Stub  
 Un objet spécifique de l’interface qui fournit le marshaling des paramètres et la communication nécessaires pour un objet d’application recevoir des appels à partir d’un client qui est en cours d’exécution dans un environnement d’exécution différents, tels que sur un thread différent ou dans un autre processus. Le stub se trouve à l’objet application et communique avec un proxy correspondant se trouve avec le client qui l’appelle. Voir aussi proxy.  
  
 sous-nœud  
 Consultez les enfants.  
  
 opération synchrone  
 Une opération démarrée par du code qui se termine avant que l’opération suivante peut démarrer. Voir aussi l’opération asynchrone.  
  
## <a name="t-z"></a>T-Z  
 trEE  
 Une structure qui représente une relation hiérarchique entre les éléments (nœuds). Il existe un nœud au niveau supérieur d’une arborescence (racine). En dessous de la racine, il peut y avoir plusieurs enfants. Chaque enfant peut être à son tour le parent d’autres enfants, constituant ainsi des ramifications comme un arbre. Un dossier contenant des documents et autres dossiers est un exemple typique d’une structure arborescente. Voir aussi hiérarchie, nœud, racine, enfant, parent.  
  
 Serveur Web  
 Un ordinateur qui fournit des services Web et les pages pour les utilisateurs d’Internet et intranet.

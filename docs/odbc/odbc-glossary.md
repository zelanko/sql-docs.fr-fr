---
title: Glossaire ODBC ( Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], glossary
- glossary [ODBC]
ms.assetid: e8227000-1944-42e5-a881-1f549e1ff9d1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ac454a8c57fe6e2f12724440dc37c3a1953e4c85
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302900"
---
# <a name="odbc-glossary"></a>Glossaire ODBC
## <a name="a"></a>Un  
 **plan d’accès**  
 Un plan généré par le moteur de base de données pour exécuter un relevé SQL. Équivalent au code exécutable compilé à partir d’une langue de troisième génération comme C.  
  
 **fonction globale**  
 Une fonction qui génère une valeur unique à partir d’un groupe de valeurs, souvent utilisée avec les clauses **GROUP BY** et **HAVING.** Les fonctions agrégées incluent **AVG**, **COUNT**, **MAX**, **MIN**, et **SUM**. Aussi connu sous le nom *de fonctions définies*. *Voir aussi* la fonction scalaire.  
  
 **ANSI**  
 Institut national de normalisation de l’Amérique. L’API ODBC est basée sur l’interface de niveau d’appel ANSI.  
  
 **APD**  
 *Voir* le descripteur de paramètres d’application (APD).  
  
 **API**  
 Interface de programmation d’applications. Un ensemble de routines qu’une application utilise pour demander et exécuter des services de niveau inférieur. L’API ODBC est composée des fonctions de l’ODBC.  
  
 **application**  
 Un programme exécutable qui appelle fonctionne dans l’API ODBC.  
  
 **descripteur de paramètre d’application (APD)**  
 Un descripteur qui décrit les paramètres dynamiques utilisés dans une déclaration SQL avant toute conversion spécifiée par l’application.  
  
 **descripteur de ligne d’application (ARD)**  
 Un descripteur qui représente les métadonnées et les données de la colonne dans les tampons de l’application, décrivant une série de données à la suite de toute conversion de données spécifiée par l’application.  
  
 **Ard**  
 *Voir* le descripteur de la ligne d’application (ARD).  
  
 **mode auto-commit**  
 Un mode de validation de transaction dans lequel les transactions sont validées immédiatement après leur exécution.  
  
## <a name="b"></a>B  
 **changement comportemental**  
 Un changement dans certaines fonctionnalités du comportement ODBC *3.x* au comportement D’ODBC *2.x,* ou vice versa. Causé par la modification de l’attribut SQL_ATTR_ODBC_VERSION environnement.  
  
 **Grand objet binaire (BLOB)**  
 Toutes les données binaires sur un certain nombre d’octets, tels que 255. Typiquement beaucoup plus longtemps. Ces données sont généralement envoyées et récupérées à partir de la source de données en parties. Aussi connu sous le nom *de données longues*.  
  
 **Contraignant**  
 Comme verbe, l’acte d’associer une colonne dans un ensemble de résultats ou un paramètre dans une déclaration SQL avec une variable d’application. En tant que nom, l’association.  
  
 **compensation contraignante**  
 Une valeur ajoutée aux adresses tampon de données et aux adresses tampons longueur/indicateur pour toutes les données de colonne ou de paramètres liées, produisant de nouvelles adresses.  
  
 **curseur de bloc**  
 Un curseur capable d’aller chercher plus d’une rangée de données à la fois.  
  
 **buffer**  
 Une mémoire d’application utilisée pour transmettre des données entre l’application et le conducteur. Les tampons se présentent souvent par paires : un *tampon de données* et un tampon de longueur de *données.*  
  
 **byte**  
 Huit bits ou un octet. *Voir aussi* octet.  
  
## <a name="c"></a>C  
 **Type de données C**  
 Le type de données d’une variable dans un programme C, dans ce cas, l’application.  
  
 **Catalogue**  
 L’ensemble de tables système dans une base de données qui décrivent la forme de la base de données. Aussi connu sous le nom de *schéma* ou *dictionnaire de données*.  
  
 **fonction catalogue**  
 Une fonction ODBC utilisée pour récupérer des informations dans le catalogue de la base de données.  
  
 **INTERFACE DE LIGNE DE COMMANDE**  
 *Voir* Api.  
  
 **client/serveur**  
 Une stratégie d’accès à la base de données dans laquelle un ou plusieurs clients accèdent aux données via un serveur. Les clients implémentent généralement l’interface utilisateur pendant que le serveur contrôle l’accès à la base de données.  
  
 **Colonne**  
 Le conteneur pour un seul élément d’information d’affilée. Aussi connu sous *le nom de champ*.  
  
 **Commettre**  
 Pour rendre permanentes les modifications d’une transaction.  
  
 **Concurrence**  
 La capacité de plus d’une transaction d’accéder aux mêmes données en même temps.  
  
 **niveau de conformité**  
 Un ensemble discret de fonctionnalités pris en charge par un pilote ou une source de données. ODBC définit les niveaux de conformation de l’API et les niveaux de conformité SQL.  
  
 **connection**  
 Un cas particulier d’un conducteur et d’une source de données.  
  
 **navigation de connexion**  
 Rechercher le réseau à la recherche de sources de données pour se connecter. La navigation de connexion peut comporter plusieurs étapes. Par exemple, l’utilisateur peut d’abord parcourir le réseau pour les serveurs, puis naviguer sur un serveur particulier pour une base de données.  
  
 **poignée de connexion**  
 Une poignée à une structure de données qui contient des informations sur une connexion.  
  
 **ligne actuelle**  
 La ligne actuellement pointée par le curseur. Les opérations positionnées agissent sur la ligne actuelle.  
  
 **Curseur**  
 Un logiciel qui renvoie des rangées de données à l’application. Probablement nommé d’après le curseur clignotant sur un terminal informatique; tout comme ce curseur indique la position actuelle sur l’écran, un curseur sur un ensemble de résultats indique la position actuelle dans l’ensemble de résultat.  
  
## <a name="d"></a>D  
 **mémoire tampon de données**  
 Un tampon utilisé pour passer les données. Souvent associé à un tampon de données est un *tampon de longueur de données*.  
  
 **dictionnaire de données**  
 *Voir* catalogue.  
  
 **mémoire tampon de longueur de données**  
 Un tampon utilisé pour passer la longueur de la valeur dans un *tampon de données*correspondant . Le tampon de longueur de données est également utilisé pour stocker des indicateurs, par exemple si la valeur des données est annulée.  
  
 **source de données**  
 Les données auxquelles l’utilisateur souhaite accéder et son système d’exploitation associé, DBMS et la plate-forme réseau (le cas échéant).  
  
 **type de données**  
 Le type de pièce de données. ODBC définit les types de données C et SQL. *Voir aussi* l’indicateur de type.  
  
 **colonne de données à l’exécution**  
 Une colonne pour laquelle les données sont envoyées après **SQLSetPos** est appelée. Ainsi nommé parce que les données sont envoyées au moment de l’exécution plutôt que d’être placé dans un tampon rowset. Les données longues sont généralement envoyées en pièces au moment de l’exécution.  
  
 **paramètre de données à l’exécution**  
 Un paramètre pour lequel les données sont envoyées après **SQLExecute** ou **SQLExecDirect** est appelé. Ainsi nommé parce que les données sont envoyées lorsque la déclaration SQL est exécutée plutôt que d’être placé dans un tampon de paramètres. Les données longues sont généralement envoyées en pièces au moment de l’exécution.  
  
 **Base**  
 Une collecte discrète de données dans un DBMS. Aussi un DBMS.  
  
 **moteur de base de données**  
 Le logiciel d’un DBMS qui analyse et exécute les déclarations SQL et accède aux données physiques.  
  
 **Sgbd**  
 Système de gestion des bases de données. Couche logicielle entre la base de données physique et l'utilisateur. Le SGBD (système de gestion de base de données) gère tous les accès à la base de données.  
  
 **Pilote basé sur DBMS**  
 Un conducteur qui accède aux données physiques par l’intermédiaire d’un moteur de base de données autonome.  
  
 **DDL**  
 Langage de définition des données. Ces déclarations dans SQL qui définissent, par opposition à manipuler, les données. Par exemple, **CREATE TABLE**, **CREATE INDEX**, **GRANT**, et **REVOKE**.  
  
 **identificateur délimité**  
 Un identifiant qui est inclus dans les caractères de citation d’identification afin qu’il puisse contenir des caractères spéciaux ou assortir des mots clés (également connu sous le nom d’identifiant cité).  
  
 **Descripteur**  
 Une structure de données qui contient des informations sur les données de colonne ou les paramètres dynamiques. La représentation physique du descripteur n’est pas définie; les applications n’ont un accès direct à un descripteur qu’en manipulant ses champs en appelant les fonctions ODBC avec la poignée descripteur.  
  
 **base de données de bureau**  
 Un DBMS conçu pour fonctionner sur un ordinateur personnel. En général, ces DBMS ne fournissent pas de moteur de base de données autonome et doivent être consultés par l’intermédiaire d’un pilote basé sur des fichiers. Les moteurs de ces pilotes ont généralement réduit le soutien à SQL et aux transactions. Par exemple, dBASE, Paradox, Btrieve ou Microsoft® FoxPro®.  
  
 **diagnostic**  
 Un enregistrement contenant des informations diagnostiques sur la dernière fonction appelée qui utilisait une poignée particulière. Les dossiers diagnostiques sont associés aux poignées de l’environnement, de la connexion, de l’énoncé et du descripteur.  
  
 **DML**  
 Langage de manipulation de données. Ces déclarations dans SQL qui manipulent, par opposition à définir, les données. Par exemple, **INSERT**, **UPDATE**, **DELETE**, et **SELECT**.  
  
 **Pilote**  
 Une bibliothèque de routine qui expose les fonctions dans l’API ODBC. Les conducteurs sont spécifiques à un seul DBMS.  
  
 **Gestionnaire de pilote**  
 Une bibliothèque de routine qui gère l’accès aux chauffeurs pour l’application. Le gestionnaire de conducteur charge et décharge (ou se connecte et se déconnecte) des pilotes et transmet les appels aux fonctions ODBC au bon conducteur.  
  
 **installation du pilote DLL**  
 Un DLL qui contient des fonctions d’installation et de configuration spécifiques au conducteur.  
  
 **curseur dynamique**  
 Un curseur défilementable capable de détecter les lignes mises à jour, supprimées ou insérées dans l’ensemble de résultats.  
  
 **dynamique SQL**  
 Un type de SQL intégré dans lequel les déclarations SQL sont créées et compilées au moment de l’exécution. *Voir aussi* SQL statique.  
  
## <a name="e"></a>E  
 **SQL intégré**  
 Les déclarations SQL qui sont incluses directement dans un programme écrit dans une autre langue, comme COBOL ou C. ODBC n’utilise pas sqL intégré. *Voir aussi* SQL statique *et* SQL dynamique.  
  
 **Environnement**  
 Un contexte mondial dans lequel accéder aux données; associé à l’environnement est toute information de nature mondiale, comme une liste de toutes les connexions dans cet environnement.  
  
 **poignée de l’environnement**  
 Une poignée à une structure de données qui contient des informations sur l’environnement.  
  
 **clause d’évasion**  
 Une clause dans une déclaration sqL.  
  
 **Exécuter**  
 Pour exécuter une déclaration SQL.  
  
## <a name="f"></a>F  
 **curseur de graisse**  
 *Voir* curseur de bloc.  
  
 **Chercher**  
 Pour récupérer une ou plusieurs lignes d’un ensemble de résultats.  
  
 **Champ**  
 *Voir* la colonne.  
  
 **pilote basé sur des fichiers**  
 Un conducteur qui accède directement aux données physiques. Dans ce cas, le conducteur contient un moteur de base de données et agit à la fois comme conducteur et source de données.  
  
 **source de données de fichier**  
 Une source de données pour laquelle les informations de connexion sont stockées dans un fichier .dsn.  
  
 **clé étrangère**  
 Une colonne ou des colonnes dans une table qui correspondent à la clé principale dans une autre table.  
  
 **curseur à l’avant seulement**  
 Un curseur qui ne peut aller de l’avant que par l’ensemble de résultats et ne récupère généralement qu’une seule rangée à la fois. La plupart des bases de données relationnelles ne prennent en charge que les curseurs avant-seulement.  
  
## <a name="h"></a>H  
 **Poignée**  
 Une valeur qui identifie de façon unique quelque chose comme un fichier ou une structure de données. Les poignées ne sont significatives que pour le logiciel qui les crée et les utilise, mais sont transmises par d’autres logiciels pour identifier les choses. ODBC définit les poignées pour les environnements, les connexions, les déclarations et les descripteurs.  
  
## <a name="i"></a>I  
 **descripteur de paramètre de mise en œuvre (IPD)**  
 Un descripteur qui décrit les paramètres dynamiques utilisés dans une déclaration SQL après toute conversion spécifiée par l’application.  
  
 **descripteur de ligne de mise en œuvre (IRD)**  
 Un descripteur qui décrit une série de données avant toute conversion spécifiée par l’application.  
  
 **installateur DLL**  
 Un DLL qui installe des composants ODBC et configure les sources de données.  
  
 **Facilité d’amélioration de l’intégrité**  
 Un sous-ensemble de SQL conçu pour maintenir l’intégrité d’une base de données.  
  
 **niveau de conformation de l’interface**  
 Le niveau de l’interface ODBC 3.7 supportée par un conducteur; peut être de base, de niveau 1 ou de niveau 2.  
  
 **Interopérabilité**  
 La possibilité d’une application d’utiliser le même code lors de l’accès aux données dans différents DBMS.  
  
 **IPD**  
 *Voir* Descripteur paramètre de mise en œuvre (IPD).  
  
 **Ird**  
 *Voir* Implémentation Descriptor de ligne (IRD).  
  
 **ISO/IEC**  
 Organisation internationale des normes/Commission électrotechnique internationale. L’API ODBC est basée sur l’interface de niveau d’appel ISO/IEC.  
  
## <a name="j"></a>J  
 **Rejoindre**  
 Une opération dans une base de données relationnelle qui relie les lignes en deux tableaux ou plus en faisant correspondre les valeurs dans des colonnes spécifiées.  
  
## <a name="k"></a>K  
 **key**  
 Une colonne ou des colonnes dont les valeurs identifient une ligne. *Voir aussi* clé étrangère *et* clé principale.  
  
 **keyset (keyset)**  
 Un ensemble de touches utilisées par un curseur mixte ou à clé pour réfélérer les rangées.  
  
 **curseur de jeu de clés**  
 Un curseur défilementable qui détecte les lignes mises à jour et supprimées à l’aide d’un jeu de clés.  
  
## <a name="l"></a>L  
 **Littérale**  
 Représentation de caractère d’une valeur réelle des données dans une déclaration SQL.  
  
 **Verrouillage**  
 Le processus par lequel un DBMS restreint l’accès à une rangée dans un environnement multi-plus. Le DBMS se définit généralement un peu sur une rangée ou la page physique contenant une ligne qui indique que la ligne ou la page est verrouillée.  
  
 **données longues**  
 Toutes les données binaires ou de caractère sur une certaine longueur, telles que 255 octets ou caractères. Typiquement beaucoup plus longtemps. Ces données sont généralement envoyées et récupérées à partir de la source de données en parties. Aussi connu sous le nom *bloB*s ou *CLOB*s.  
  
## <a name="m"></a>M  
 **source de données de la machine**  
 Une source de données pour laquelle les informations de connexion sont stockées sur le système (par exemple, le registre).  
  
 **mode de validation manuelle**  
 Un mode de validation de transaction dans lequel les transactions doivent être explicitement validées en appelant **SQLTransact**.  
  
 **Métadonnées**  
 Données qui décrivent un paramètre dans une déclaration SQL ou une colonne dans un ensemble de résultats. Par exemple, le type de données, la longueur des bytes et la précision d’un paramètre.  
  
 **pilote à plusieurs niveaux**  
 *Voir* pilote basé sur DBMS.  
  
## <a name="n"></a>N  
 **Valeur NULL**  
 N’ayant pas de valeur explicitement assignée. En particulier, une valeur NULL est différente d’un zéro ou d’un blanc.  
  
## <a name="o"></a>O  
 **octet**  
 Huit bits ou un octet. *Voir aussi* byte.  
  
 **longueur d’octet**  
 La longueur dans les octets d’un tampon ou les données qu’il contient.  
  
 **ODBC**  
 Connectivité de base de données ouverte. Spécification d’une API qui définit un ensemble standard de routines avec lesquelles une application peut accéder aux données dans une source de données.  
  
 **Administrateur de l’ODBC**  
 Un programme exécutable qui appelle l’installateur DLL pour configurer les sources de données.  
  
 Ouvrir le groupe  
 Une entreprise qui publie des normes. Elle publie notamment les normes SQL Access Group (SAG).  
  
 **concurrence optimiste**  
 Une stratégie visant à accroître la concurrence dans laquelle les lignes ne sont pas verrouillées. Au lieu de cela, avant qu’ils ne soient mis à jour ou supprimés, un curseur vérifie s’ils ont été changés depuis leur dernière lecture. Si c’est le cas, la mise à jour ou la suppression échoue. *Voir aussi* la concordance pessimiste.  
  
 **jointure extérieure**  
 Une jointure dans laquelle les lignes assorties et non-retouches sont retournées. Les valeurs de toutes les colonnes de la table inégalée en rangées nonmatching sont réglées à NULL.  
  
 **Propriétaire**  
 Le propriétaire d’une table.  
  
## <a name="p"></a>P  
 **Paramètre**  
 Une variable dans une déclaration SQL, marquée d’un marqueur de paramètres ou d’un point d’interrogation (?). Les paramètres sont liés aux variables d’application et à leurs valeurs récupérées lors de l’exécution de l’instruction.  
  
 **descripteur de paramètre**  
 Un descripteur qui décrit les paramètres de temps d’exécution utilisés dans une déclaration SQL, soit avant toute conversion spécifiée par l’application (un descripteur de paramètre d’application, ou APD) ou après toute conversion spécifiée par l’application (un descripteur de paramètres de mise en œuvre, ou IPD).  
  
 **tableau de fonctionnement des paramètres**  
 Un tableau contenant des valeurs qu’une application peut définir pour indiquer que le paramètre correspondant doit être ignoré dans une opération **SQLExecDirect** ou **SQLExecute.**  
  
 **tableau de statut de paramètre**  
 Un tableau contenant l’état d’un paramètre après un appel à **SQLExecDirect** ou **SQLExecute**.  
  
 **accès concurrentiel pessimiste**  
 Une stratégie pour la mise en œuvre de la sérialisation, dans laquelle les lignes sont verrouillées afin que d’autres transactions ne puissent pas les modifier. *Voir aussi* la concurrence optimiste *et* la sérialisation.  
  
 **opération positionnée**  
 Toute opération qui agit sur la ligne actuelle. Par exemple, les relevés de mise à jour et de suppression positionnés, **SQLGetData**et **SQLSetPos**.  
  
 **énoncé de mise à jour positionné**  
 Une déclaration SQL utilisée pour mettre à jour les valeurs dans la rangée actuelle.  
  
 **déclaration de suppression positionnée**  
 Une déclaration SQL utilisée pour supprimer la ligne actuelle.  
  
 **Préparer**  
 Pour compiler une déclaration SQL. Un plan d’accès est créé en préparant une déclaration SQL.  
  
 **clé principale**  
 Une colonne ou des colonnes qui identifie uniquement une ligne dans une table.  
  
 **Procédure**  
 Un groupe d’un ou plusieurs relevés SQL précalculés qui sont stockés comme objet désigné dans une base de données.  
  
 **colonne de procédure**  
 Un argument dans un appel de procédure, la valeur retournée par une procédure, ou une colonne dans un résultat défini par une procédure.  
  
## <a name="q"></a>Q  
 **Qualification**  
 Une base de données qui contient une ou plusieurs tables.  
  
 **Requête**  
 Une déclaration SQL. Parfois utilisé pour signifier une déclaration **SELECT.**  
  
 **identificateur entre guillemets**  
 Un identifiant qui est inclus dans les caractères de citation d’identification afin qu’il puisse contenir des caractères spéciaux ou assortir des mots clés (également connu dans SQL-92 comme un identifiant délimité).  
  
## <a name="r"></a>R  
 **Radix**  
 La base d’un système de nombres. Habituellement 2 ou 10.  
  
 **enregistrement**  
 *Voir la* rangée.  
  
 **ensemble de résultats**  
 L’ensemble de lignes créées par l’exécution d’une déclaration **SELECT.**  
  
 **code de retour**  
 La valeur retournée par une fonction ODBC.  
  
 **restaurer**  
 Pour retourner les valeurs modifiées par une transaction à leur état d’origine.  
  
 **Ligne**  
 Un ensemble de colonnes connexes qui décrivent une entité spécifique. Aussi connu comme un *enregistrement*.  
  
 **descripteur de ligne**  
 Un descripteur qui décrit les colonnes d’un ensemble de résultats, soit avant toute conversion spécifiée par l’application (un descripteur de ligne de mise en œuvre, ou IRD) ou après toute conversion spécifiée par l’application (un descripteur de ligne d’application, ou ARD).  
  
 **tableau d’opération de ligne**  
 Un tableau contenant des valeurs qu’une application peut définir pour indiquer que la ligne correspondante doit être ignorée dans une opération **SQLSetPos.**  
  
 **tableau de statut de la ligne**  
 Un tableau contenant l’état d’une rangée après un appel à **SQLFetch**, **SQLFetchScroll**, ou **SQLSetPos**.  
  
 **Rowset**  
 L’ensemble de rangées est retourné en un seul aller par un curseur de bloc.  
  
 **tampons en rangée**  
 Les tampons liés aux colonnes d’un ensemble de résultats et dans lesquels les données pour un ensemble entier de rangées sont retournées.  
  
## <a name="s"></a>S  
 **Sag**  
 *Voir* SqL Access Group (SAG).  
  
 **fonction scalaire**  
 Une fonction qui génère une valeur unique à partir d’une seule valeur. Par exemple, une fonction qui modifie le cas des données de caractère.  
  
 **schéma**  
 *Voir* catalogue.  
  
 **curseur défilant**  
 Un curseur qui peut avancer ou reculer à travers l’ensemble de résultats.  
  
 **sérialisation**  
 Que deux transactions exécutant simultanément produisent un résultat identique à celui de l’exécution en série (ou séquentielle) de ces transactions. Les transactions sérialisables sont nécessaires pour maintenir l’intégrité de la base de données.  
  
 **base de données serveur**  
 Un DBMS conçu pour être exécuté dans un environnement client/serveur. Ces DBMS fournissent un moteur de base de données autonome qui fournit un soutien riche pour SQL et les transactions. Ils sont accessibles par l’intermédiaire de pilotes basés sur DBMS. Par exemple, Oracle, Informix, DB/2, ou Microsoft® SQL Server.  
  
 **fonction d’ensemble**  
 *Voir la* fonction globale.  
  
 **configuration DLL**  
 *Voir* la configuration du pilote DLL *et* la configuration du traducteur DLL.  
  
 **pilote à un seul niveau**  
 *Voir* le pilote basé sur les fichiers.  
  
 **SQL**  
 Langage de requête structurée. Un langage utilisé par les bases de données relationnelles pour interroger, mettre à jour et gérer les données.  
  
 **Groupe d’accès SQL (SAG)**  
 Un consortium industriel d’entreprises concernées par SQL DBMS. L’interface call-Level du Groupe Ouvert est basée sur les travaux effectués à l’origine par le groupe d’accès SQL.  
  
 **Niveau de conformité SQL**  
 Le niveau de grammaire SQL-92 supporté par un conducteur; peut être l’entrée, FIPS Transition, Intermédiaire, ou Plein.  
  
 **Type de données SQL**  
 Le type de données d’une colonne ou d’un paramètre tel qu’il est stocké dans la source de données.  
  
 **SQLSTATE**  
 Une valeur de cinq caractères qui indique une erreur particulière.  
  
 **Déclaration SQL**  
 Une phrase complète dans SQL qui commence par un mot clé et décrit complètement une action à prendre. Par exemple, SELECT - FROM Orders. Les déclarations de SQL ne doivent pas être confondues avec les déclarations.  
  
 **État**  
 Une condition bien définie d’un élément. Par exemple, une connexion comporte sept États, y compris des données non allouées, allouées, connectées et nécessitant des données. Certaines opérations ne peuvent être effectuées que lorsqu’un élément est dans un état particulier. Par exemple, une connexion ne peut être libérée que lorsqu’elle est dans un état attribué et non, par exemple, lorsqu’elle se trouve dans un état connecté.  
  
 **transition de l’État**  
 Le mouvement d’un élément d’un état à l’autre. ODBC définit les transitions rigoureuses de l’État pour les environnements, les connexions et les déclarations.  
  
 **Déclaration**  
 Un conteneur pour toutes les informations liées à un communiqué de SQL. Les déclarations ne doivent pas être confondues avec les déclarations de SQL.  
  
 **poignée de déclaration**  
 Une poignée à une structure de données qui contient des informations sur une déclaration.  
  
 **curseur statique**  
 Un curseur défilementable qui ne peut pas détecter les mises à jour, supprime ou insère dans l’ensemble de résultats. Habituellement mis en œuvre en faisant une copie de l’ensemble de résultat.  
  
 **SQL statique**  
 Un type de SQL intégré dans lequel les déclarations SQL sont codées et compilées lorsque le reste du programme est compilé. *Voir aussi* SQL dynamique.  
  
 **procédure stockée**  
 *Voir* la procédure.  
  
## <a name="t"></a>T  
 **table**  
 Une collection de rangées.  
  
 **Thunking**  
 La conversion d’adresses 16 bits en adresses 32 bits, ou vice versa, lorsque des applications 16 bits sont utilisées avec des pilotes ODBC 32 bits.  
  
 **Transaction**  
 Une unité atomique de travail. Le travail dans une transaction doit être entièrement effectué. Si une partie de la transaction échoue, la transaction entière échoue.  
  
 **isolement des transactions**  
 L’acte d’isoler une transaction des effets de toutes les autres transactions.  
  
 **niveau d’isolement des transactions**  
 Une mesure de la façon dont une transaction est isolée. Il y a cinq niveaux d’isolement des transactions : Lire non engagé, lire, lire, réaltérant, sérialiser et versionr.  
  
 **traducteur DLL**  
 Un DLL utilisé pour traduire les données d’un personnage réglé à un autre.  
  
 **installation de traducteur DLL**  
 Un DLL qui contient des fonctions d’installation et de configuration spécifiques aux traducteurs.  
  
 **validation en deux temps**  
 Processus d’engagement d’une transaction distribuée en deux phases. Dans la première phase, le processeur de transaction vérifie que toutes les parties de la transaction peuvent être validées. Dans la deuxième phase, toutes les parties de la transaction sont engagées. Si une partie de la transaction indique dans la première phase qu’elle ne peut pas être engagée, la deuxième phase ne se produit pas. ODBC ne prend pas en charge les commits en deux phases.  
  
 **indicateur de type**  
 Une valeur d’intégreur a été transmise ou retournée d’une fonction ODBC pour indiquer le type de données d’une variable d’application, un paramètre ou une colonne. ODBC définit les indicateurs de type pour les types de données C et SQL.  
  
## <a name="v"></a>V  
 **Vue**  
 Une autre façon de voir les données dans un ou plusieurs tableaux. Une vue est généralement créée comme un sous-ensemble des colonnes à partir d’une ou plusieurs tables. Dans ODBC, les vues sont généralement équivalentes aux tables.

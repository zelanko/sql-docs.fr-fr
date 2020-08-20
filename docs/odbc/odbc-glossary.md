---
description: Glossaire ODBC
title: Glossaire ODBC | Microsoft Docs
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
ms.openlocfilehash: 57b08d48944ee288b4eba849917828b6fe1d4396
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466251"
---
# <a name="odbc-glossary"></a>Glossaire ODBC
## <a name="a"></a>Un  
 **plan d’accès**  
 Plan généré par le moteur de base de données pour exécuter une instruction SQL. Équivalent au code exécutable compilé à partir d’un langage de troisième génération comme C.  
  
 **fonction d’agrégation**  
 Fonction qui génère une valeur unique à partir d’un groupe de valeurs, souvent utilisée avec les clauses **Group by** et **having** . Les fonctions d’agrégation incluent **AVG**, **Count**, **Max**, **min**et **Sum**. Également appelées *fonctions set*. *Voir aussi* fonction scalaire.  
  
 **ANSI**  
 American National Standards Institute. L’API ODBC est basée sur l’interface au niveau de l’appel ANSI.  
  
 **APD**  
 *Voir* descripteur de paramètre d’application (APD).  
  
 **API**  
 Interface de programmation d’applications. Ensemble de routines qu’une application utilise pour demander et exécuter des services de niveau inférieur. L’API ODBC est composée des fonctions ODBC.  
  
 **application**  
 Programme exécutable qui appelle des fonctions dans l’API ODBC.  
  
 **descripteur de paramètre d’application (APD)**  
 Descripteur qui décrit les paramètres dynamiques utilisés dans une instruction SQL avant toute conversion spécifiée par l’application.  
  
 **descripteur de ligne d’application (ARD)**  
 Descripteur qui représente les métadonnées de colonne et les données dans les mémoires tampons de l’application, décrivant une ligne de données après toute conversion de données spécifiée par l’application.  
  
 **ARD**  
 *Voir* descripteur de ligne d’application (ARD).  
  
 **mode de validation automatique**  
 Mode de validation de transaction dans lequel les transactions sont validées immédiatement après leur exécution.  
  
## <a name="b"></a>B  
 **changement de comportement**  
 Modification de certaines fonctionnalités du comportement ODBC *3. x* au comportement ODBC *2. x* , ou vice versa. Provoqué par la modification de l’attribut d’environnement SQL_ATTR_ODBC_VERSION.  
  
 **Objet BLOB (Binary Large Object)**  
 Toutes les données binaires sur un certain nombre d’octets, par exemple 255. Généralement plus longtemps. Ces données sont généralement envoyées et récupérées de la source de données en plusieurs parties. Également appelées *données de type long*.  
  
 **liant**  
 En tant que verbe, action consistant à associer une colonne dans un jeu de résultats ou un paramètre dans une instruction SQL à une variable d’application. En tant que nom, l’Association.  
  
 **décalage de liaison**  
 Valeur ajoutée aux adresses de tampon de données et aux adresses de tampon de longueur/d’indicateur pour toutes les données de colonne ou de paramètre liées, en produisant de nouvelles adresses.  
  
 **curseur de bloc**  
 Curseur permettant l’extraction de plusieurs lignes de données à la fois.  
  
 **mémoire tampon**  
 Une partie de la mémoire d’application utilisée pour passer des données entre l’application et le pilote. Les mémoires tampons sont souvent des paires : une *mémoire tampon de données* et une *mémoire tampon de longueur de données*.  
  
 **byte**  
 Huit bits ou 1 octet. *Voir aussi* octet.  
  
## <a name="c"></a>C  
 **Type de données C**  
 Le type de données d’une variable dans un programme C, dans ce cas l’application.  
  
 **catalog**  
 Ensemble des tables système dans une base de données qui décrivent la forme de la base de données. Également connu sous le nom de *dictionnaire de données*ou de *schéma* .  
  
 **fonction de catalogue**  
 Fonction ODBC utilisée pour récupérer des informations à partir du catalogue de la base de données.  
  
 **INTERFACE DE LIGNE DE COMMANDE**  
 *Consultez* MobileVBActiveX.  
  
 **client/serveur**  
 Stratégie d’accès à la base de données dans laquelle un ou plusieurs clients accèdent aux données via un serveur. Les clients implémentent généralement l’interface utilisateur pendant que le serveur contrôle l’accès aux bases de données.  
  
 **column**  
 Conteneur pour un seul élément d’information dans une ligne. Également connu sous le nom de *champ*.  
  
 **valider**  
 Pour rendre permanentes les modifications dans une transaction.  
  
 **concurrency**  
 Capacité de plusieurs transactions à accéder aux mêmes données en même temps.  
  
 **niveau de conformité**  
 Ensemble discret de fonctionnalités prises en charge par un pilote ou une source de données. ODBC définit les niveaux de conformité de l’API et les niveaux de conformité SQL.  
  
 **connection**  
 Instance particulière d’un pilote et d’une source de données.  
  
 **exploration des connexions**  
 Recherche de sources de données pour se connecter au réseau. L’exploration des connexions peut impliquer plusieurs étapes. Par exemple, l’utilisateur peut d’abord Rechercher des serveurs sur le réseau, puis rechercher une base de données sur un serveur particulier.  
  
 **handle de connexion**  
 Handle vers une structure de données qui contient des informations sur une connexion.  
  
 **ligne actuelle**  
 Ligne actuellement vers laquelle pointe le curseur. Les opérations positionnées agissent sur la ligne actuelle.  
  
 **cursor**  
 Élément logiciel qui renvoie des lignes de données à l’application. Probablement nommé après le curseur clignotant sur un terminal informatique ; tout comme le curseur indique la position actuelle sur l’écran, un curseur sur un jeu de résultats indique la position actuelle dans le jeu de résultats.  
  
## <a name="d"></a>D  
 **mémoire tampon de données**  
 Mémoire tampon utilisée pour passer des données. Une mémoire tampon de *longueur de données*est souvent associée à une mémoire tampon de données.  
  
 **dictionnaire de données**  
 *Consultez* le catalogue.  
  
 **mémoire tampon de longueur des données**  
 Mémoire tampon utilisée pour passer la longueur de la valeur dans une *mémoire tampon de données*correspondante. La mémoire tampon de longueur des données est également utilisée pour stocker des indicateurs, par exemple si la valeur des données est terminée par un caractère null.  
  
 **source de données**  
 Les données auxquelles l’utilisateur souhaite accéder et le système d’exploitation, le SGBD et la plateforme réseau qui lui sont associés (le cas échéant).  
  
 **type de données**  
 Type d’un élément de données. ODBC définit les types de données C et SQL. *Voir aussi* indicateur de type.  
  
 **colonne de données en cours d’exécution**  
 Colonne pour laquelle les données sont envoyées après l’appel de **SQLSetPos** . Ainsi nommé, car les données sont envoyées au moment de l’exécution au lieu d’être placées dans une mémoire tampon d’ensemble de lignes. Les données de type long sont généralement envoyées en parties au moment de l’exécution.  
  
 **paramètre de données en cours d’exécution**  
 Paramètre pour lequel les données sont envoyées après l’appel de **SQLExecute** ou **SQLExecDirect** . Ainsi nommé, car les données sont envoyées lors de l’exécution de l’instruction SQL au lieu d’être placées dans une mémoire tampon de paramètres. Les données de type long sont généralement envoyées en parties au moment de l’exécution.  
  
 **database**  
 Collection discrète de données dans un SGBD. Également un SGBD.  
  
 **moteur de base de données**  
 Le logiciel dans un SGBD qui analyse et exécute des instructions SQL et accède aux données physiques.  
  
 **GÈRENT**  
 Système de gestion de base de données. Couche logicielle entre la base de données physique et l'utilisateur. Le SGBD (système de gestion de base de données) gère tous les accès à la base de données.  
  
 **Pilote SGBD**  
 Pilote qui accède aux données physiques via un moteur de base de données autonome.  
  
 **DDL**  
 Langage de définition de données. Les instructions dans SQL qui définissent, par opposition à manipuler, les données. Par exemple, **Create table**, **créer un index**, **accorder**et **révoquer**.  
  
 **identificateur délimité**  
 Identificateur placé entre guillemets pour qu’il puisse contenir des caractères spéciaux ou des mots clés de correspondance (également appelés identificateur entre guillemets).  
  
 **Description**  
 Structure de données qui contient des informations sur les données de colonne ou les paramètres dynamiques. La représentation physique du descripteur n’est pas définie. les applications accèdent directement à un descripteur en manipulant ses champs en appelant des fonctions ODBC avec le handle de descripteur.  
  
 **base de données de bureau**  
 SGBD conçu pour s’exécuter sur un ordinateur personnel. En règle générale, ces SGBD ne fournissent pas de moteur de base de données autonome et doivent être accessibles par le biais d’un pilote basé sur des fichiers. Les moteurs de ces pilotes ont généralement une prise en charge réduite de SQL et des transactions. Par exemple, dBASE, Paradox, Btrieve ou Microsoft® FoxPro®.  
  
 **diagnostic**  
 Enregistrement contenant des informations de diagnostic sur la dernière fonction appelée qui utilisait un handle particulier. Les enregistrements de diagnostic sont associés à des handles d’environnement, de connexion, d’instruction et de descripteur.  
  
 **DML**  
 Langage de manipulation de données. Les instructions dans SQL qui manipulent, au lieu de définir, des données. Par exemple, **Insérer**, **mettre à jour**, **supprimer**et **Sélectionner**.  
  
 **pilote**  
 Bibliothèque de routines qui expose les fonctions de l’API ODBC. Les pilotes sont spécifiques à un seul SGBD.  
  
 **Gestionnaire de pilote**  
 Bibliothèque de routines qui gère l’accès aux pilotes pour l’application. Le gestionnaire de pilotes charge et décharge (ou se connecte aux pilotes et se déconnecte) et passe les appels aux fonctions ODBC au pilote approprié.  
  
 **DLL d’installation du pilote**  
 DLL qui contient des fonctions d’installation et de configuration spécifiques au pilote.  
  
 **curseur dynamique**  
 Curseur de défilement pouvant détecter les lignes mises à jour, supprimées ou insérées dans le jeu de résultats.  
  
 **SQL dynamique**  
 Type de SQL incorporé dans lequel les instructions SQL sont créées et compilées au moment de l’exécution. *Voir aussi* SQL statique.  
  
## <a name="e"></a>E  
 **Embedded SQL**  
 Les instructions SQL qui sont incluses directement dans un programme écrit dans un autre langage, tel que COBOL ou C. ODBC, n’utilisent pas EmbeddedSQL. *Voir aussi* SQL statique *et* SQL dynamique.  
  
 **environment**  
 Contexte global dans lequel accéder aux données ; les informations globales sont associées à l’environnement, par exemple une liste de toutes les connexions dans cet environnement.  
  
 **handle d’environnement**  
 Handle d’une structure de données qui contient des informations sur l’environnement.  
  
 **Escape (clause)**  
 Une clause dans une instruction SQL.  
  
 **effectue**  
 Pour exécuter une instruction SQL.  
  
## <a name="f"></a>F  
 **curseur FAT**  
 *Consultez* bloquer le curseur.  
  
 **collecté**  
 Pour récupérer une ou plusieurs lignes d’un jeu de résultats.  
  
 **case**  
 *Consultez* la colonne.  
  
 **pilote basé sur des fichiers**  
 Pilote qui accède directement aux données physiques. Dans ce cas, le pilote contient un moteur de base de données et agit en tant que pilote et source de données.  
  
 **source de données de fichier**  
 Source de données pour laquelle les informations de connexion sont stockées dans un fichier. DSN.  
  
 **clé étrangère**  
 Colonne ou colonnes dans une table qui correspondent à la clé primaire d’une autre table.  
  
 **curseur avant uniquement**  
 Curseur qui peut uniquement avancer dans le jeu de résultats et extrait généralement une seule ligne à la fois. La plupart des bases de données relationnelles ne prennent en charge que les curseurs avant uniquement.  
  
## <a name="h"></a>H  
 **traitée**  
 Valeur qui identifie de façon unique un nom de fichier ou de structure de données. Les handles sont significatifs uniquement pour le logiciel qui les crée et les utilise, mais qui sont passés par d’autres logiciels pour identifier les choses. ODBC définit des handles pour les environnements, les connexions, les instructions et les descripteurs.  
  
## <a name="i"></a>I  
 **descripteur de paramètre d’implémentation (IPD)**  
 Descripteur qui décrit les paramètres dynamiques utilisés dans une instruction SQL après toute conversion spécifiée par l’application.  
  
 **descripteur de ligne d’implémentation (IRD)**  
 Descripteur qui décrit une ligne de données avant toute conversion spécifiée par l’application.  
  
 **DLL du programme d’installation**  
 DLL qui installe les composants ODBC et configure les sources de données.  
  
 **Fonctionnalité d’amélioration de l’intégrité**  
 Sous-ensemble de SQL conçu pour assurer l’intégrité d’une base de données.  
  
 **niveau de conformité de l’interface**  
 Le niveau de l’interface ODBC 3,7 pris en charge par un pilote ; peut être Core, Level 1 ou Level 2.  
  
 **interopérabilité**  
 Capacité d’une application à utiliser le même code lors de l’accès aux données dans différents SGBD.  
  
 **IPD**  
 *Consultez* Descripteur de paramètre d’implémentation (IPD).  
  
 **IRD**  
 *Consultez* Descripteur de ligne d’implémentation (IRD).  
  
 **ISO/IEC**  
 International Standards Organization/Commission Électrotechnique Internationale. L’API ODBC est basée sur l’interface de niveau d’appel ISO/IEC.  
  
## <a name="j"></a>J  
 **join**  
 Opération dans une base de données relationnelle qui lie les lignes d’au moins deux tables en faisant correspondre les valeurs dans les colonnes spécifiées.  
  
## <a name="k"></a>K  
 **key**  
 Colonne ou colonnes dont les valeurs identifient une ligne. *Voir aussi* clé étrangère *et* clé primaire.  
  
 **ensembles**  
 Ensemble de clés utilisé par un curseur mixte ou KEYSET pour récupérer des lignes.  
  
 **curseur de jeu de clés**  
 Curseur de défilement qui détecte les lignes mises à jour et supprimées à l’aide d’un jeu de clés.  
  
## <a name="l"></a>L  
 **literal**  
 Représentation sous forme de caractère d’une valeur de données réelle dans une instruction SQL.  
  
 **Verr**  
 Processus par lequel un SGBD restreint l’accès à une ligne dans un environnement multi-utilisateur. Le SGBD définit généralement un bit sur une ligne ou sur la page physique contenant une ligne qui indique que la ligne ou la page est verrouillée.  
  
 **données de type long**  
 Toutes les données binaires ou de caractères sur une certaine longueur, par exemple 255 octets ou caractères. Généralement plus longtemps. Ces données sont généralement envoyées et récupérées de la source de données en plusieurs parties. Également connu sous le nom de *BLOB*s ou *CLOB*s.  
  
## <a name="m"></a>M  
 **source de données de l’ordinateur**  
 Source de données pour laquelle les informations de connexion sont stockées sur le système (par exemple, le registre).  
  
 **mode de validation manuelle**  
 Mode de validation de transaction dans lequel les transactions doivent être validées explicitement en appelant **SQLTransact**.  
  
 **métadonnées**  
 Données qui décrivent un paramètre dans une instruction SQL ou une colonne dans un jeu de résultats. Par exemple, le type de données, la longueur d’octet et la précision d’un paramètre.  
  
 **pilote à plusieurs niveaux**  
 *Consultez* Pilote basé sur le SGBD.  
  
## <a name="n"></a>N  
 **Valeur NULL**  
 N’ayant aucune valeur assignée explicitement. En particulier, une valeur NULL est différente d’un zéro ou d’un espace.  
  
## <a name="o"></a>O  
 **poids**  
 Huit bits ou 1 octet. *Voir aussi* Byte.  
  
 **longueur en octets**  
 Longueur en octets d’une mémoire tampon ou des données qu’elle contient.  
  
 **ODBC**  
 Open Database Connectivity. Spécification pour une API qui définit un ensemble standard de routines auxquelles une application peut accéder aux données dans une source de données.  
  
 **Administrateur ODBC**  
 Programme exécutable qui appelle la DLL du programme d’installation pour configurer des sources de données.  
  
 Ouvrir le groupe  
 Société qui publie les normes. En particulier, il publie les normes de groupe d’accès SQL (SAG).  
  
 **accès concurrentiel optimiste**  
 Stratégie pour augmenter l’accès concurrentiel dans laquelle les lignes ne sont pas verrouillées. Au lieu de cela, avant qu’elles ne soient mises à jour ou supprimées, un curseur vérifie s’ils ont été modifiés depuis leur dernière lecture. Si c’est le cas, la mise à jour ou la suppression échoue. *Voir aussi* accès concurrentiel pessimiste.  
  
 **jointure externe**  
 Jointure dans laquelle les deux lignes de correspondance et de non-correspondance sont retournées. Les valeurs de toutes les colonnes de la table sans correspondance dans les lignes sans correspondance ont la valeur NULL.  
  
 **du**  
 Propriétaire d’une table.  
  
## <a name="p"></a>P  
 **paramètre**  
 Variable dans une instruction SQL, marquée avec un marqueur de paramètre ou un point d’interrogation ( ?). Les paramètres sont liés aux variables d’application et à leurs valeurs extraites lors de l’exécution de l’instruction.  
  
 **descripteur de paramètre**  
 Descripteur qui décrit les paramètres d’exécution utilisés dans une instruction SQL, avant toute conversion spécifiée par l’application (descripteur de paramètre d’application ou APD) ou après toute conversion spécifiée par l’application (un descripteur de paramètre d’implémentation ou un IPD).  
  
 **Tableau des opérations sur les paramètres**  
 Tableau contenant les valeurs qu’une application peut définir pour indiquer que le paramètre correspondant doit être ignoré dans une opération **SQLExecDirect** ou **SQLExecute** .  
  
 **Tableau d’état des paramètres**  
 Tableau qui contient l’état d’un paramètre après un appel à **SQLExecDirect** ou **SQLExecute**.  
  
 **l’accès concurrentiel pessimiste ;**  
 Stratégie d’implémentation de la sérialisation, dans laquelle les lignes sont verrouillées de sorte que les autres transactions ne puissent pas les modifier. *Voir aussi* accès concurrentiel optimiste *et* sérialisation.  
  
 **opération positionnée**  
 Toute opération qui agit sur la ligne actuelle. Par exemple, les instructions Update et DELETE positionnées, **SQLGetData**et **SQLSetPos**.  
  
 **instruction Update positionnée**  
 Instruction SQL utilisée pour mettre à jour les valeurs de la ligne actuelle.  
  
 **instruction DELETE positionnée**  
 Instruction SQL utilisée pour supprimer la ligne actuelle.  
  
 **préparation**  
 Pour compiler une instruction SQL. Un plan d’accès est créé en préparant une instruction SQL.  
  
 **clé primaire**  
 Colonne ou colonnes qui identifient de façon unique une ligne dans une table.  
  
 **procédures**  
 Groupe d’une ou de plusieurs instructions SQL précompilées qui sont stockées sous la forme d’un objet nommé dans une base de données.  
  
 **colonne procédure**  
 Un argument dans un appel de procédure, la valeur retournée par une procédure ou une colonne dans un jeu de résultats créé par une procédure.  
  
## <a name="q"></a>Q  
 **qualificateur**  
 Base de données qui contient une ou plusieurs tables.  
  
 **query**  
 Instruction SQL. Parfois utilisé pour signifier une instruction **Select** .  
  
 **identificateur entre guillemets**  
 Identificateur placé entre guillemets pour qu’il puisse contenir des caractères spéciaux ou des mots clés de correspondance (également connu sous le nom d’identificateur délimité dans SQL-92).  
  
## <a name="r"></a>R  
 **dicaux**  
 Base d’un système de nombres. Généralement 2 ou 10.  
  
 **enregistrement**  
 *Consultez* la ligne.  
  
 **jeu de résultats**  
 Ensemble de lignes créées en exécutant une instruction **Select** .  
  
 **Code de retour**  
 Valeur retournée par une fonction ODBC.  
  
 **restaurer**  
 Pour retourner les valeurs modifiées par une transaction à leur état d’origine.  
  
 **haut**  
 Ensemble de colonnes associées qui décrivent une entité spécifique. Également appelé *enregistrement*.  
  
 **descripteur de ligne**  
 Descripteur qui décrit les colonnes d’un jeu de résultats, avant toute conversion spécifiée par l’application (descripteur de ligne d’implémentation ou IRD) ou après toute conversion spécifiée par l’application (un descripteur de ligne d’application ou ARD).  
  
 **Tableau d’opérations de ligne**  
 Tableau contenant les valeurs qu’une application peut définir pour indiquer que la ligne correspondante doit être ignorée dans une opération **SQLSetPos** .  
  
 **Tableau d’état de ligne**  
 Tableau qui contient l’état d’une ligne après un appel à **SQLFetch**, **SQLFetchScroll**ou **SQLSetPos**.  
  
 **OpenXml**  
 Ensemble de lignes retourné dans une extraction unique par un curseur de bloc.  
  
 **mémoires tampons d’ensemble de lignes**  
 Mémoires tampons liées aux colonnes d’un jeu de résultats et dans lesquelles les données d’un ensemble de lignes entier sont retournées.  
  
## <a name="s"></a>S  
 **SAG**  
 *Consultez* Groupe d’accès SQL (SAG).  
  
 **fonction scalaire**  
 Fonction qui génère une valeur unique à partir d’une valeur unique. Par exemple, une fonction qui modifie la casse des données caractères.  
  
 **schéma**  
 *Consultez* le catalogue.  
  
 **curseur à défilement**  
 Curseur qui peut avancer ou reculer dans le jeu de résultats.  
  
 **sérialisation**  
 Si deux transactions qui s’exécutent simultanément produisent un résultat qui est le même que l’exécution en série (ou séquentielle) de ces transactions. Les transactions sérialisables sont requises pour assurer l’intégrité de la base de données.  
  
 **base de données du serveur**  
 SGBD conçu pour être exécuté dans un environnement client/serveur. Ces SGBD fournissent un moteur de base de données autonome qui offre une prise en charge enrichie de SQL et des transactions. Ils sont accessibles via des pilotes basés sur SGBD. Par exemple, Oracle, Informix, DB/2 ou Microsoft® SQL Server.  
  
 **Set, fonction**  
 *Consultez* fonction d’agrégation.  
  
 **DLL d’installation**  
 *Consultez* dll d’installation du pilote *et* dll d’installation du convertisseur.  
  
 **pilote à un seul niveau**  
 *Consultez* pilote basé sur des fichiers.  
  
 **SQL**  
 langage SQL. Langage utilisé par les bases de données relationnelles pour interroger, mettre à jour et gérer des données.  
  
 **Groupe d’accès SQL (SAG)**  
 Un consortium industriel d’entreprises soucieuses des SGBD SQL. L’interface au niveau de l’appel du groupe ouvert est basée sur le travail initialement effectué par le groupe d’accès SQL.  
  
 **Niveau de conformité SQL**  
 Le niveau de grammaire SQL-92 pris en charge par un pilote ; peut être Entry, FIPS Transitional, Intermediate ou Full.  
  
 **Type de données SQL**  
 Type de données d’une colonne ou d’un paramètre, tel qu’il est stocké dans la source de données.  
  
 **SQLSTATE**  
 Valeur à cinq caractères qui indique une erreur particulière.  
  
 **Instruction SQL**  
 Expression complète en SQL qui commence par un mot clé et décrit complètement une action à entreprendre. Par exemple, sélectionnez * dans Orders. Les instructions SQL ne doivent pas être confondues avec des instructions.  
  
 **state**  
 Condition bien définie d’un élément. Par exemple, une connexion a sept États, y compris les données non allouées, allouées, connectées et nécessitant des données. Certaines opérations ne peuvent être effectuées que lorsqu’un élément est dans un état particulier. Par exemple, une connexion peut être libérée uniquement lorsqu’elle est dans un État alloué et non, par exemple, quand elle est dans un état connecté.  
  
 **transition d’État**  
 Déplacement d’un élément d’un État à un autre. ODBC définit des transitions d’État rigoureuses pour les environnements, les connexions et les instructions.  
  
 **instruction**  
 Conteneur pour toutes les informations relatives à une instruction SQL. Les instructions ne doivent pas être confondues avec des instructions SQL.  
  
 **descripteur d’instruction**  
 Handle d’une structure de données qui contient des informations sur une instruction.  
  
 **curseur statique**  
 Curseur de défilement qui ne peut pas détecter les mises à jour, les suppressions ou les insertions dans le jeu de résultats. Généralement implémentée en effectuant une copie du jeu de résultats.  
  
 **SQL statique**  
 Type de code SQL incorporé dans lequel les instructions SQL sont codées en dur et compilées lors de la compilation du reste du programme. *Voir aussi* SQL dynamique.  
  
 **procédure stockée**  
 *Consultez* la procédure.  
  
## <a name="t"></a>T  
 **table**  
 Collection de lignes.  
  
 **thunking**  
 La conversion d’adresses 16 bits en adresses 32 bits, ou vice versa, lorsque les applications 16 bits sont utilisées avec les pilotes ODBC 32 bits.  
  
 **transaction**  
 Une unité atomique de travail. Le travail dans une transaction doit être entièrement effectué. Si une partie de la transaction échoue, la transaction entière échoue.  
  
 **isolation des transactions**  
 Action consistant à isoler une transaction des effets de toutes les autres transactions.  
  
 **niveau d’isolation de la transaction**  
 Mesure de l’isolement d’une transaction. Il existe cinq niveaux d’isolement des transactions : lecture non validée, lecture validée, lecture renouvelable, sérialisable et contrôle de version.  
  
 **DLL du traducteur**  
 DLL utilisée pour convertir les données d’un jeu de caractères à un autre.  
  
 **DLL d’installation du traducteur**  
 DLL qui contient des fonctions d’installation et de configuration spécifiques au convertisseur.  
  
 **validation en deux phases**  
 Processus de validation d’une transaction distribuée en deux phases. Dans la première phase, le processeur de transactions vérifie que toutes les parties de la transaction peuvent être validées. Dans la deuxième phase, toutes les parties de la transaction sont validées. Si une partie de la transaction indique, dans la première phase, qu’elle ne peut pas être validée, la deuxième phase ne se produit pas. ODBC ne prend pas en charge les validations en deux phases.  
  
 **indicateur de type**  
 Valeur entière passée à ou retournée à partir d’une fonction ODBC pour indiquer le type de données d’une variable d’application, d’un paramètre ou d’une colonne. ODBC définit des indicateurs de type pour les types de données C et SQL.  
  
## <a name="v"></a>V  
 **affichage**  
 Autre façon de consulter les données dans une ou plusieurs tables. Une vue est généralement créée en tant que sous-ensemble de colonnes d’une ou plusieurs tables. Dans ODBC, les vues sont généralement équivalentes aux tables.

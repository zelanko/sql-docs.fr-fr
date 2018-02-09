---
title: "Mise à jour - se connecter à la documentation de SQL Server | Documents Microsoft"
description: "Extraits de l’affichage de contenu mis à jour pour obtenir une documentation récemment modifié, pour se connecter à Microsoft SQL Server."
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.prod_service: sql-non-specified
ms.component: connect
ms.date: 02/03/2018
ms.openlocfilehash: cc4eb05dc4dcd74623c8ce7dfa7b7842449d79b6
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="new-and-recently-updated-connect-to-sql-server"></a>Nouveaux et mis à jour récemment : se connecter à SQL Server



Presque tous les jours Microsoft met à jour certains de ses articles existants sur son [Docs.Microsoft.com](http://docs.microsoft.com/) site Web de documentation. Cet article affiche des extraits d’articles récemment mis à jour. Des liens vers nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme est exécuté à nouveau régulièrement. Parfois un extrait peut apparaître avec mise en forme imparfait, ou en tant que markdown de l’article de la source. Les images ne sont jamais affichés ici.

Mises à jour récentes sont signalés pour la plage de dates suivante et l’objet :



- *Plage de dates de mises à jour :* &nbsp; **2017-12-03** &nbsp; - à - &nbsp; **2018-02-03**
- *Zone de sujet :* &nbsp; **se connecter à SQL Server**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nouveaux Articles vient d’être créés

Les liens suivants renvoient aux nouveaux articles ajoutés récemment.


***Il n’y a aucun nouvel article.***



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articles mis à jour avec des extraits

Cette section affiche les extraits des mises à jour collectés dans des articles qui ont récemment fait l’objet d’une mise à jour importante.

Les extraits affichés ici apparaissent séparés à partir de leur contexte sémantique spécifique. En outre, parfois un extrait est séparé à partir de la syntaxe markdown important qui l’entoure dans l’article. Par conséquent, ces extraits sont pour des conseils généraux. Les extraits permettent uniquement de savoir si votre intérêt justifie pris le temps de cliquer sur et consultez l’article.

Pour celles-ci et d’autres raisons, ne pas copier le code à partir de ces extraits et ne prennent pas en tant que vérité exacte tout extrait de texte. Au lieu de cela, consultez l’article.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Liste compacte d’Articles récemment mis à jour

Cette liste compacte fournit des liens vers tous les articles mis à jour qui sont répertoriés dans la section des extraits.

1. [Utilisation du chiffrement intégral avec le pilote ODBC pour SQL Server](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-using-always-encrypted-with-the-odbc-driver-for-sql-serverodbcusing-always-encrypted-with-the-odbc-drivermd"></a>1. &nbsp;[Utilisation du chiffrement intégral avec le pilote ODBC pour SQL Server](odbc/using-always-encrypted-with-the-odbc-driver.md)

*Mise à jour : 2018-01-22* &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; 

<!-- Source markdown line 524.  ms.author= "v-chojas".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 a52abae2a8f27c3b5bc411ef758610116a608f9f 352368eb269b98ab5ca3a9791fae2e70bf26277a  (PR=4686  ,  Filename=using-always-encrypted-with-the-odbc-driver.md  ,  Dirpath=docs\connect\odbc\  ,  MergeCommitSha40=82c9868b5bf95e5b0c68137ba434ddd37fc61072) -->



**Récupérer des données dans des parties avec SQLGetData**

Avant le 17 du pilote ODBC pour SQL Server, cryptage caractère et les colonnes de type binary ne sont pas accessibles dans des parties avec SQLGetData. Un seul appel de SQLGetData peut être effectué, avec une mémoire tampon de longueur suffisante pour contenir les données de la colonne entière.

**Envoyer des données dans des parties avec SQLPutData**

Impossible d’envoyer les données de comparaison ou insertion dans des parties avec SQLPutData. Un seul appel à SQLPutData peut être effectué, avec une mémoire tampon contenant la totalité des données. Pour insérer des données de type long dans les colonnes chiffrées, utilisez l’API de copie en bloc, décrit dans la section suivante, avec un fichier de données d’entrée.

**Smallmoney et money chiffrée**

Chiffré **money** ou **smallmoney** colonnes ne peut pas être ciblés par les paramètres, car il n’existe aucun spécifique qui correspond à ces types, ce qui entraîne des erreurs de conflit de Type opérande de type de données ODBC.

**Copie en bloc des colonnes chiffrées**


Utilisation de la [des fonctions de copie en bloc SQL](odbc/../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md) et le **bcp** utilitaire est pris en charge avec Always Encrypted depuis le 17 du pilote ODBC pour SQL Server. Texte en clair (insertion chiffrée sur et récupération déchiffrée sur) et texte chiffré (transféré textuellement) peuvent être insérés et récupérés à l’aide de la copie en bloc (bcp_ *) API et la **bcp** utilitaire.

- Pour récupérer du texte chiffré sous forme de varbinary (max) (par exemple, pour le chargement en masse dans une autre base de données), de se connecter sans le `ColumnEncryption` option (ou la valeur `Disabled`) et effectuer une opération BCP OUT.

- Pour insérer, extraire en texte clair et permettent d’effectuer en toute transparence le chiffrement et le déchiffrement en tant que paramètre requis, le pilote `ColumnEncryption` à `Enabled` est suffisante. Les fonctionnalités de l’API BCP sont inchangée.

- Pour insérer du texte chiffré sous forme de varbinary (max) (par exemple, tel que récupéré ci-dessus), définissez la `BCPMODIFYENCRYPTED` option sur TRUE et effectuer une opération BCP IN. Dans l’ordre pour les données résultantes être decryptable, assurez-vous que la destination clé de la colonne est la même que celle à partir de laquelle le texte chiffré obtenu à l’origine.







## <a name="similar-articles-about-new-or-updated-articles"></a>Articles similaires sur les articles nouveaux ou mis à jour

Cette section liste les articles très similaires récemment mis à jour dans d’autres domaines, dans notre dépôt public GitHub.com : [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).


#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Zones de sujet qui *faire* ont nouveaux ou récemment mis à jour articles


- [Nouveau + mis à jour (1 + 3) :&nbsp; **avancées d’Analytique pour SQL** documents](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nouveau + mis à jour (0 + 1) :&nbsp; **système de plateforme d’Analytique pour SQL** documents](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nouveau + mis à jour (0 + 1) :&nbsp; **se connecter à SQL** documents](../connect/new-updated-connect.md)
- [Nouveau + mis à jour (0 + 1) :&nbsp; **moteur de base de données pour SQL** documents](../database-engine/new-updated-database-engine.md)
- [Nouveau + mis à jour (12 + 1) : **Integration Services pour SQL** documents](../integration-services/new-updated-integration-services.md)
- [Nouveau + mis à jour (6 + 2) :&nbsp; **Linux pour SQL** documents](../linux/new-updated-linux.md)
- [Nouveau + mis à jour (15 + 0) : **PowerShell pour SQL** documents](../powershell/new-updated-powershell.md)
- [Nouveau + mis à jour (2 + 9) :&nbsp; **des bases de données relationnelles pour SQL** documents](../relational-databases/new-updated-relational-databases.md)
- [Nouveau + mis à jour (1 + 0) :&nbsp; **Reporting Services pour SQL** documents](../reporting-services/new-updated-reporting-services.md)
- [Nouveau + mis à jour (1 + 1) :&nbsp; **SQL opérations Studio** documents](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nouveau + mis à jour (1 + 1) :&nbsp; **Microsoft SQL Server** documents](../sql-server/new-updated-sql-server.md)
- [Nouveau + mis à jour (0 + 1) :&nbsp; **SQL Server Data Tools (SSDT)** documents](../ssdt/new-updated-ssdt.md)
- [Nouveau + mis à jour (1 + 2) :&nbsp; **SQL Server Management Studio (SSMS)** documents](../ssms/new-updated-ssms.md)
- [Nouveau + mis à jour (0 + 2) :&nbsp; **Transact-SQL** documents](../t-sql/new-updated-t-sql.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Zones de font l’objet *pas* ont tous nouveaux ou récemment mis à jour articles


- [Nouveaux + Mis à jour (0 + 0) : **Data Migration Assistant (DMA) pour SQL** (documentation)](../dma/new-updated-dma.md)
- [Nouveau + mis à jour (0 0 +) : **ActiveX Data Objects (ADO) pour SQL** documents](../ado/new-updated-ado.md)
- [Nouveaux + Mis à jour (0 + 0) : **Analysis Services pour SQL** (documentation)](../analysis-services/new-updated-analysis-services.md)
- [Nouveau + mis à jour (0 0 +) : **Data Quality Services pour SQL** documents](../data-quality-services/new-updated-data-quality-services.md)
- [Nouveau + mis à jour (0 0 +) : **Extensions DMX (Data Mining) pour SQL** documents](../dmx/new-updated-dmx.md)
- [Nouveaux + Mis à jour (0 + 0) : **Master Data Services (MDS) for SQL** (documentation)](../master-data-services/new-updated-master-data-services.md)
- [Nouveau + mis à jour (0 0 +) : **MDX (Multidimensional Expressions) pour SQL** documents](../mdx/new-updated-mdx.md)
- [Nouveau + mis à jour (0 0 +) : **ODBC (Open Database Connectivity) pour SQL** documents](../odbc/new-updated-odbc.md)
- [Nouveau + mis à jour (0 0 +) : **exemples pour SQL** documents](../sample/new-updated-sample.md)
- [Nouveau + mis à jour (0 0 +) : **SQL Server Migration Assistant (SSMA)** documents](../ssma/new-updated-ssma.md)
- [Nouveaux + Mis à jour (0 + 0) : **Outils pour SQL** (documentation)](../tools/new-updated-tools.md)
- [Nouveau + mis à jour (0 0 +) : **XQuery pour SQL** documents](../xquery/new-updated-xquery.md)



---
title: "Mise à jour - T-SQL docs | Documents Microsoft"
description: "Extraits de l’affichage de contenu mis à jour pour obtenir une documentation récemment modifié, de Transact-SQL."
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.prod_service: sql-non-specified
ms.component: t-sql
ms.date: 02/03/2018
ms.openlocfilehash: c1f1ce751bd4bca781644e7e2f5282320c8c88a8
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="new-and-recently-updated-transact-sql-docs"></a>Nouveau et récemment mis à jour : les documents de Transact-SQL



Presque tous les jours Microsoft met à jour certains de ses articles existants sur son [Docs.Microsoft.com](http://docs.microsoft.com/) site Web de documentation. Cet article affiche des extraits d’articles récemment mis à jour. Des liens vers nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme est exécuté à nouveau régulièrement. Parfois un extrait peut apparaître avec mise en forme imparfait, ou en tant que markdown de l’article de la source. Les images ne sont jamais affichés ici.

Mises à jour récentes sont signalés pour la plage de dates suivante et l’objet :



- *Plage de dates de mises à jour :* &nbsp; **2017-12-03** &nbsp; - à - &nbsp; **2018-02-03**
- *Zone de sujet :* &nbsp; **T-SQL**.




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

1. [CREATE STATISTICS (Transact-SQL)](#TitleNum_1)
2. [UPDATE STATISTICS (Transact-SQL)](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-create-statistics-transact-sqlstatementscreate-statistics-transact-sqlmd"></a>1. &nbsp; [CREATE STATISTICS (Transact-SQL)](statements/create-statistics-transact-sql.md)

*Mise à jour : 2018-01-04* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([suivant](#TitleNum_2))

<!-- Source markdown line 200.  ms.author= "edmaca".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 384e68493597bcc36876a3c7bada2630106256e2 c22168ea59b6020e8ebe1ccac5fa6a6049e6db4d  (PR=4460  ,  Filename=create-statistics-transact-sql.md  ,  Dirpath=docs\t-sql\statements\  ,  MergeCommitSha40=4aeedbb88c60a4b035a49754eff48128714ad290) -->



MAXDOP = *max_degree_of_parallelism*
**s’applique à**: SQL Server (démarrage avec SQL Server 2017 CU3).

 Remplace le **degré maximal de parallélisme** option de configuration pour la durée de l’opération de statistiques. Pour plus d’informations, consultez [Configurer l’option de configuration du serveur Degré maximal de parallélisme](statements/../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md). Utilisez MAXDOP pour limiter le nombre de processeurs utilisés dans une exécution de plan parallèle. Le nombre maximal de processeurs est égal à 64.

 *max_degree_of_parallelism* peut être :

 1 supprime la génération de plans parallèles.

 \>1 limite le nombre maximal de processeurs utilisés dans une opération de statistiques parallèle au nombre spécifié ou inférieur en fonction de la charge système actuelle.

 0 (valeur par défaut) utilise le nombre réel de processeurs ou inférieur en fonction de la charge système actuelle.

 \<update_stats_stream_option > identifié à titre informatif uniquement. Non pris en charge. La compatibilité future n'est pas garantie.




&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-update-statistics-transact-sqlstatementsupdate-statistics-transact-sqlmd"></a>2. &nbsp;[UPDATE STATISTICS (Transact-SQL)](statements/update-statistics-transact-sql.md)

*Mise à jour : 2018-01-04* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_1))

<!-- Source markdown line 167.  ms.author= "edmaca".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 5721e21a9f43fa784fe9357c47cb2a814385e63d 24ae47c553635f389a182e5e643bf9bd6bf59e78  (PR=4460  ,  Filename=update-statistics-transact-sql.md  ,  Dirpath=docs\t-sql\statements\  ,  MergeCommitSha40=4aeedbb88c60a4b035a49754eff48128714ad290) -->



MAXDOP = *max_degree_of_parallelism*

**S’applique à**: SQL Server (à partir de SQL Server 2017 CU3).

 Remplace le **degré maximal de parallélisme** option de configuration pour la durée de l’opération de statistiques. Pour plus d’informations, consultez [Configurer l’option de configuration du serveur Degré maximal de parallélisme](statements/../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md). Utilisez MAXDOP pour limiter le nombre de processeurs utilisés dans une exécution de plan parallèle. Le nombre maximal de processeurs est égal à 64.

 *max_degree_of_parallelism* peut être :

 1 supprime la génération de plans parallèles.

 \>1 limite le nombre maximal de processeurs utilisés dans une opération de statistiques parallèle au nombre spécifié ou inférieur en fonction de la charge système actuelle.

 0 (valeur par défaut) utilise le nombre réel de processeurs ou inférieur en fonction de la charge système actuelle.








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



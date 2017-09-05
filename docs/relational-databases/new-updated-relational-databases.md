---
title: "Mise à jour - Documentation des bases de données relationnelles | Microsoft Docs"
description: "Affichage d’extraits de contenu mis à jour de la documentation récemment modifiée des bases de données relationnelles."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: BYHAM
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: relational-databases
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 07/17/2017
ms.author: genemi
ms.translationtype: HT
ms.sourcegitcommit: 71203bfa7cb4dcd06cc14ad8e49e5bc1113f8605
ms.openlocfilehash: 519fbd2bc596112dbb1c662d76e4aeeb230ffc36
ms.contentlocale: fr-fr
ms.lasthandoff: 07/31/2017

---
# <a name="new-and-recently-updated-relational-databases-docs"></a>Contenu nouveau et récemment mis à jour : documentation des bases de données relationnelles



Presque tous les jours, Microsoft met à jour certains de ses articles sur son site web de documentation [Docs.Microsoft.com](http://docs.microsoft.com/). Cet article contient des extraits d’articles récemment mis à jour. Des liens vers de nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme qui est réexécuté régulièrement. Un extrait peut parfois apparaître avec une mise en forme imparfaite ou au format Markdown de l’article source. Les images ne sont jamais affichées ici.

Les mises à jour récentes sont signalées pour la plage de dates et le sujet suivants :



- *Plage de dates des mises à jour :* &nbsp; **23-05-2017** &nbsp; - au - &nbsp; **17-07-2017**
- *Domaine :* &nbsp; **bases de données relationnelles**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nouveaux articles créés récemment

Les liens suivants renvoient aux nouveaux articles ajoutés récemment.


1. [Mécanismes internes d’OLTP en mémoire de SQL Server pour SQL Server 2016](in-memory-oltp/sql-server-in-memory-oltp-internals-for-sql-server-2016.md)
2. [Traitement de requêtes adaptatif dans les bases de données SQL](performance/adaptive-query-processing.md)
3. [Guide d’amélioration de la confidentialité et du traitement des exigences GDPR avec la plateforme Microsoft SQL](security/microsoft-sql-and-the-gdpr-requirements.md)
4. [sys.pdw_replicated_table_cache_state (Transact-SQL)](system-catalog-views/sys-pdw-replicated-table-cache-state-transact-sql.md)
5. [sys.trusted_assemblies (Transact-SQL)](system-catalog-views/sys-trusted-assemblies-transact-sql.md)
6. [sys.dm_exec_query_parallel_workers (Transact-SQL)](system-dynamic-management-views/sys-dm-exec-query-parallel-workers-transact-sql.md)
7. [sys.sp_add_trusted_assembly (Transact-SQL)](system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md)
8. [sys.sp_drop_trusted_assembly (Transact-SQL)](system-stored-procedures/sys-sp-drop-trusted-assembly-transact-sql.md)




&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Liste compacte d’articles mis à jour récemment

Cette liste compacte fournit des liens vers tous les articles mis à jour qui sont répertoriés dans la section des extraits.



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articles mis à jour avec des extraits

Cette section affiche les extraits de mises à jour collectées à partir des articles qui ont récemment subi une mise à jour importante.

Les extraits affichés ici apparaissent séparés de leur contexte sémantique propre. Un extrait est parfois séparé de la syntaxe Markdown importante qui l’entoure dans l’article. Ces extraits sont donc donnés à titre indicatif uniquement. Les extraits vous permettent seulement de savoir si les articles correspondants vont vous intéresser et si oui, de cliquer dessus pour les consulter.

Pour cela et pour d’autres raisons, ne copiez pas le code de ces extraits et ne prenez pas à la lettre les extraits de texte. Au lieu de cela, consultez l’article.



&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-altering-memory-optimized-tablesin-memory-oltpaltering-memory-optimized-tablesmd"></a>1. &nbsp; [Modification des tables à mémoire optimisée](in-memory-oltp/altering-memory-optimized-tables.md)

*Mise à jour : 23-06-2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Suivant](#TitleNum_2))

<!-- Source markdown line 82.  ms.author= "genemi".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 8359700b5db24838f1bb273526794c2865bbbe11 41d77cf0bbcf53a1b64d6524a24e5736c5a073da  (PR=2171  ,  Filename=altering-memory-optimized-tables.md  ,  Dirpath=docs\relational-databases\in-memory-oltp\  ,  MergeCommitSha40=7d2dbe0bdc4cbd05f11eacf938b35a9c35ace2e7) -->



**Journalisation d’ALTER TABLE sur des tables à mémoire optimisée**

Sur une table optimisée en mémoire, la plupart des scénarios ALTER TABLE s’exécutent désormais en parallèle, d’où une optimisation des écritures dans le journal des transactions. L’optimisation est obtenue par la journalisation des seules modifications de métadonnées dans le journal des transactions. Cependant, les opérations ALTER TABLE suivantes sont effectuées en mode à thread unique et ne sont pas optimisées pour la journalisation.

L’opération monothread dans ce cas consigne dans le journal des transactions l’intégralité du contenu de la table modifiée. Voici la liste des opérations à thread unique :

- Modifier ou ajouter une colonne pour utiliser un type d’objet volumineux (LOB) : nvarchar(max), varchar(max) ou varbinary(max).

- Ajouter ou supprimer un index COLUMNSTORE.

- Presque tout ce qui affecte une [colonne hors ligne--../../relational-databases/in-memory-oltp/supported-data-types-for-in-memory-oltp.md).

    - Provoquer le déplacement d’une colonne sur une ligne en mode hors ligne.

    - Provoquer le déplacement d’une colonne en mode hors ligne sur une ligne.

    - Créer une colonne hors ligne.

    - *Exception :* l’allongement d’une colonne déjà hors ligne est journalisé de la manière optimisée. 
  




&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-table-and-row-size-in-memory-optimized-tablesin-memory-oltptable-and-row-size-in-memory-optimized-tablesmd"></a>2. &nbsp; [Taille de la table et des lignes dans les tables à mémoire optimisée](in-memory-oltp/table-and-row-size-in-memory-optimized-tables.md)

*Mise à jour : 22-06-2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Précédent](#TitleNum_1) | [Suivant](#TitleNum_3))

<!-- Source markdown line 114.  ms.author= "genemi".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 27ce0fa2e7bb464f9c3d6e32dd195de3b79abfcd 0a3cacd86024e2b734704ffd37e55ca0b17a0c94  (PR=2163  ,  Filename=table-and-row-size-in-memory-optimized-tables.md  ,  Dirpath=docs\relational-databases\in-memory-oltp\  ,  MergeCommitSha40=fe6de2b16b9792a5399b1c014af72a2a5ee52377) -->



 
  
 Le calcul de la [taille du corps de ligne] est expliqué dans le tableau suivant.  
  
 Il existe deux calculs différents pour la taille du corps de ligne : la taille calculée et la taille réelle :  
  
-   La taille calculée, indiquée par [taille calculée du corps de ligne], est utilisée pour déterminer si la limite de taille de ligne de 8 060 octets est dépassée.  
  
-   La taille réelle, indiquée par [taille réelle du corps de ligne], est la taille de stockage réelle du corps de ligne en mémoire et dans les fichiers de point de contrôle.  
  
 Les deux tailles [taille calculée du corps de ligne] et [taille réelle du corps de ligne] sont calculées de façon similaire. La seule différence est le calcul de la taille des colonnes (n)varchar(i) et varbinary(i), comme indiqué en bas du tableau suivant. La taille calculée du corps de ligne utilise la taille déclarée *i* comme taille de la colonne, tandis que la taille réelle du corps de ligne utilise la taille réelle des données.  
  
 Le tableau suivant décrit le calcul de la taille du corps de ligne, fourni en tant que [taille réelle du corps de ligne] = SUM([taille des types superficiels]) + 2 + 2 * [nombre de colonnes de type profond].  
  
|Section|Taille|Commentaires|  
|-------------|----------|--------------|  
|Colonnes de type superficiel|SUM ([taille des types superficiels]). Les tailles en octets des différents types sont les suivantes :<br /><br /> **Bit**: 1<br /><br /> **Tinyint**: 1<br /><br /> **Smallint**: 2<br /><br /> **Int**: 4<br /><br /> **Real**: 4<br /><br /> **Smalldatetime**: 4<br /><br /> **Smallmoney**: 4<br /><br /> **Bigint**: 8<br /><br /> **Datetime**: 8<br /><br /> **Datetime2**: 8<br /><br /> **Float**: 8<br /><br /> **Money** : 8<br /><br /> **Numeric** (précision <=18) : 8<br /><br /> **Time** : 8<br /><br /> **Numeric**(précision >18) : 16<br /><br /> **Uniqueidentifier** : 16||  
|Remplissage de colonne superficielle|Les valeurs possibles sont :<br /><br /> 1 s'il y a des colonnes de type profond et la taille de données totale des colonnes superficielles est un nombre impair.<br /><br /> 0 dans les autres cas|Les types profonds sont les types (var)binary et (n)(var)char.|  




&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-post-migration-validation-and-optimization-guidepost-migration-validation-and-optimization-guidemd"></a>3. &nbsp; [Guide de validation et d’optimisation post-migration](post-migration-validation-and-optimization-guide.md)

*Mise à jour : 21-06-2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Précédent](#TitleNum_2) | [Suivant](#TitleNum_4))

<!-- Source markdown line 27.  ms.author= "harinid".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 faa2e3dd8be3aeb475bf8c7f71617ebf17969892 f2760dfecda10baeb121929b72a4d8164e81185b  (PR=2126  ,  Filename=post-migration-validation-and-optimization-guide.md  ,  Dirpath=docs\relational-databases\  ,  MergeCommitSha40=dcbeda6b8372b358b6497f78d6139cad91c8097c) -->



Voici quelques-uns des scénarios de performance courants rencontrés après la migration vers la plateforme [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)] et leur résolution. Certains de ces scénarios sont propres à la migration de [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)] vers [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)]\(des versions antérieures aux versions plus récentes), ainsi qu’à la migration d’une plateforme étrangère (comme Oracle, DB2, MySQL et Sybase) vers [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)].

**<a name="CEUpgrade"></a> Régression des requêtes en raison d’un changement de version CE**


**S’applique à :** migration de [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)] vers [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)].

Quand vous migrez d’une version antérieure de [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)] vers [!INCLUDE[ssSQL14--../includes/sssql14-md.md)] ou une version plus récente, et que vous mettez à jour le [niveau de compatibilité de base de données--../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md) vers le plus récent, une charge de travail peut être exposée à un risque de régression des performances.

Cela vient du fait qu’à compter de [!INCLUDE[ssSQL14--../includes/sssql14-md.md)], tous les changements de l’optimiseur de requête sont liés au [niveau de compatibilité de base de données--../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md) le plus récent, de sorte que les plans ne sont pas changés au moment même de la mise à niveau, mais quand un utilisateur remplace l’option de base de données `COMPATIBILITY_LEVEL` par la plus récente. Cette fonctionnalité, en association avec le magasin de requêtes, vous offre un niveau de contrôle élevé sur les performances des requêtes dans le processus de mise à niveau. 

Pour plus d’informations sur les changements apportés à l’optimiseur de requête dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)], consultez [Optimisation de vos plans de requête avec l’estimateur de cardinalité SQL Server 2014](http://msdn.microsoft.com/library/dn673537.aspx).




&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-sysquerystoreplan-transact-sqlsystem-catalog-viewssys-query-store-plan-transact-sqlmd"></a>4. &nbsp; [sys.query_store_plan (Transact-SQL)](system-catalog-views/sys-query-store-plan-transact-sql.md)

*Mise à jour : 05-06-2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Précédent](#TitleNum_3))

<!-- Source markdown line 58.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 1b77e34309ba7033578b3c82ed83c8c2fbc93e24 ce4ade9ab906c35cb87068a1fb91c4e1d7549aac  (PR=1940  ,  Filename=sys-query-store-plan-transact-sql.md  ,  Dirpath=docs\relational-databases\system-catalog-views\  ,  MergeCommitSha40=1d363db8e8bd0e1460cdea3c3a7add68e48714c9) -->



**Limites de l'application forcée d'un plan**

Le Magasin des requêtes a un mécanisme qui permet de forcer l’optimiseur de requête à utiliser un certain plan d’exécution. Toutefois, il existe certaines limitations qui peuvent empêcher l’application d’un plan. 

Premièrement, si le plan contient les constructions suivantes :
* Instruction Insert bulk.
* Instruction Insert bulk.
* Référence à une table externe
* Requête distribuée ou opérations de recherche en texte intégral
* Utilisation de requêtes globales 
* Curseurs
* Spécification de jointure en étoile non valide 

Deuxièmement, quand les objets sur lesquels s’appuie le plan ne sont plus disponibles :
* Base de données (si la base de données d'où provient le plan n’existe plus)
* Index (absent ou désactivé)

Enfin, s’il y a des problèmes avec le plan lui-même :
* Non conforme pour la requête
* L’optimiseur de requête a dépassé le nombre d’opérations autorisées
* Code XML du plan incorrect





<a name="similars2"/>

&nbsp;

## <a name="similar-articles"></a>Articles similaires

Cette section liste les articles très similaires récemment mis à jour dans d’autres domaines, dans le même dépôt GitHub.com : [MicrosoftDocs/**sql-docs-pr**](https://github.com/microsoftdocs/sql-docs-pr/).

<!--  20170717-1101  -->

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Domaines avec des articles nouveaux ou mis à jour récemment

- [Nouveaux + Mis à jour (4 + 4) : **Analyse avancée pour SQL** (documentation)](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nouveaux + Mis à jour (2 + 0) : **Analysis Services pour SQL** (documentation)](../analysis-services/new-updated-analysis-services.md)
- [Nouveaux + Mis à jour (1 + 2) : **Connexion à SQL** (documentation)](../connect/new-updated-connect.md)
- [Nouveaux + Mis à jour (6 + 0) : **Moteur de base de données pour SQL** (documentation)](../database-engine/new-updated-database-engine.md)
- [Nouveaux + Mis à jour (13 + 2) : **Linux pour SQL** (documentation)](../linux/new-updated-linux.md)
- [Nouveaux + Mis à jour (1 + 0) : **MDS (Master Data Services) pour SQL** (documentation)](../master-data-services/new-updated-master-data-services.md)
- [Nouveaux + Mis à jour (1 + 0) : **ODBC (Open Database Connectivity) pour SQL** (documentation)](../odbc/new-updated-odbc.md)
- [Nouveaux + Mis à jour (8 + 4) : **Bases de données relationnelles pour SQL** (documentation)](../relational-databases/new-updated-relational-databases.md)
- [Nouveaux + Mis à jour (2 + 2) : **Microsoft SQL Server** (documentation)](../sql-server/new-updated-sql-server.md)
- [Nouveaux + Mis à jour (0 + 1) : **SQL Server Management Studio (SSMS)** (documentation)](../ssms/new-updated-ssms.md)
- [Nouveaux + Mis à jour (1 + 0) : **Transact-SQL** (documentation)](../t-sql/new-updated-t-sql.md)
- [Nouveaux + Mis à jour (1 + 0) : **Outils pour SQL** (documentation)](../tools/new-updated-tools.md)


#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Domaines sans article nouveau ou mis à jour récemment

- [Nouveaux + Mis à jour (0 + 0) : **ActiveX Data Objects (ADO) pour SQL** (documentation)](../ado/new-updated-ado.md)
- [Nouveaux + Mis à jour (0 + 0) : **Data Quality Services pour SQL** (documentation)](../data-quality-services/new-updated-data-quality-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Extensions DMX (Data Mining Extensions) pour SQL** (documentation)](../dmx/new-updated-dmx.md)
- [Nouveaux + Mis à jour (0 + 0) : **Integration Services pour SQL** (documentation)](../integration-services/new-updated-integration-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Expressions MDX (Multidimensional Expressions) pour SQL** (documentation)](../mdx/new-updated-mdx.md)
- [Nouveaux + Mis à jour (0 + 0) : **PowerShell pour SQL** (documentation)](../powershell/new-updated-powershell.md)
- [Nouveaux + Mis à jour (0 + 0) : **Reporting Services pour SQL** (documentation)](../reporting-services/new-updated-reporting-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Exemples pour SQL** (documentation)](../sample/new-updated-sample.md)
- [Nouveaux + Mis à jour (0 + 0) : **SQL Server Data Tools (SSDT)** (documentation)](../ssdt/new-updated-ssdt.md)
- [Nouveaux + Mis à jour (0 + 0) : **SQL Server Migration Assistant (SSMA)** (documentation)](../ssma/new-updated-ssma.md)
- [Nouveaux + Mis à jour (0 + 0) : **XQuery pour SQL** (documentation)](../xquery/new-updated-xquery.md)


&nbsp;



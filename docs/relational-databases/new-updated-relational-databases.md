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
ms.date: 09/11/2017
ms.author: genemi
ms.translationtype: HT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: ee7d66bcd8720234f4aec97d24ce16ed21888a3c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/13/2017

---
# <a name="new-and-recently-updated-relational-databases-docs"></a>Contenu nouveau et récemment mis à jour : documentation des bases de données relationnelles



Presque tous les jours, Microsoft met à jour certains de ses articles sur son site web de documentation [Docs.Microsoft.com](http://docs.microsoft.com/). Cet article contient des extraits d’articles récemment mis à jour. Des liens vers de nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme qui est réexécuté régulièrement. Un extrait peut parfois apparaître avec une mise en forme imparfaite ou au format Markdown de l’article source. Les images ne sont jamais affichées ici.

Les mises à jour récentes sont signalées pour la plage de dates et le sujet suivants :



- *Période des mises à jour :* &nbsp; **18-07-2017** &nbsp; au &nbsp; **11-09-2017**
- *Domaine :* &nbsp; **bases de données relationnelles**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nouveaux articles créés récemment

Les liens suivants renvoient aux nouveaux articles ajoutés récemment.


1. [Importer des données d’Excel vers SQL Server ou Azure SQL Database](import-export/import-data-from-excel-to-sql.md)
2. [Résoudre les problèmes de connectivité de PolyBase Kerberos](polybase/polybase-troubleshoot-connectivity.md)
3. [Transparent Data Encryption (TDE)](security/encryption/transparent-data-encryption.md)
4. [Transparent Data Encryption pour Azure SQL Database et Data Warehouse](security/encryption/transparent-data-encryption-azure-sql.md)
5. [Transparent Data Encryption avec prise en charge de BYOK pour Azure SQL Database et Data Warehouse](security/encryption/transparent-data-encryption-byok-azure-sql.md)
6. [PowerShell : Activer Transparent Data Encryption à l’aide de votre propre clé Azure Key Vault](security/encryption/transparent-data-encryption-byok-azure-sql-configure.md)
7. [Effectuer une rotation du protecteur TDE (Transparent Data Encryption) à l’aide de PowerShell](security/encryption/transparent-data-encryption-byok-azure-sql-key-rotation.md)
8. [Supprimer un protecteur TDE (Transparent Data Encryption) à l’aide de PowerShell](security/encryption/transparent-data-encryption-byok-azure-sql-remove-tde-protector.md)
9. [Termes du contrat de licence SQL Server Shared Management Objects (SMO)](server-management-objects-smo/smo-license-terms.md)
10. [sys.external_libraries (Transact-SQL)](system-catalog-views/sys-external-libraries-transact-sql.md)
11. [sys.external_library_files (Transact-SQL)](system-catalog-views/sys-external-library-files-transact-sql.md)
12. [sp_rxPredict](system-stored-procedures/sp-rxpredict-transact-sql.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articles mis à jour avec des extraits

Cette section affiche les extraits des mises à jour collectés dans des articles qui ont récemment fait l’objet d’une mise à jour importante.

Les extraits affichés ici apparaissent séparés de leur contexte sémantique propre. Un extrait est parfois séparé de la syntaxe Markdown importante qui l’entoure dans l’article. Ces extraits sont donc donnés à titre indicatif uniquement. Les extraits vous permettent seulement de savoir si les articles correspondants vont vous intéresser et si oui, de cliquer dessus pour les consulter.

Pour cela et pour d’autres raisons, ne copiez pas le code de ces extraits et ne prenez pas à la lettre les extraits de texte. Consultez plutôt l’article.





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Liste compacte d’articles mis à jour récemment

Cette liste compacte fournit des liens vers tous les articles mis à jour qui sont répertoriés dans la section des extraits.

1. [Paramétrage automatique](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-automatic-tuningautomatic-tuningautomatic-tuningmd"></a>1. &nbsp; [Réglage automatique](automatic-tuning/automatic-tuning.md)

*Date de mise à jour : 16-08-2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 64.  ms.author= "jovanpop".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 be765a1acf9bdfd5485520d16160677583e81f8e 135d926227094374e6ec5484e7babee625b44bb2  (PR=2860  ,  Filename=automatic-tuning.md  ,  Dirpath=docs\relational-databases\automatic-tuning\  ,  MergeCommitSha40=e4a6157cb56c6db911406585f841046a431eef99) -->



**Correction automatique du choix de plan**


..!NCLUDE-NotShown--ssde_md--../../includes/ssde_md.md)] peut automatiquement basculer vers le dernier bon plan connu quand il détecte une régression de choix de plan.

![SQL plan choice correction--media/force-last-good-plan.png "Correction du choix de plan SQL")

..!NCLUDE-NotShown--ssde_md--../../includes/ssde_md.md)] détecte automatiquement une régression de choix de plan potentielle, notamment le plan à utiliser à la place du plan inapproprié.
Quand ..!NCLUDE-NotShown--ssde_md--../../includes/ssde_md.md)] applique le dernier bon plan connu, il surveille automatiquement les performances du plan forcé. Si le plan forcé n’est pas meilleur que le plan régressé, l’obligation d’utiliser le nouveau plan est annulée et ..!NCLUDE-NotShown--ssde_md--../../includes/ssde_md.md)] compile un nouveau plan. Si ..!NCLUDE-NotShown--ssde_md--../../includes/ssde_md.md)] détermine que le plan forcé est préférable au plan régressé, il conserve le plan forcé jusqu’à une recompilation ultérieure (par exemple, à la prochaine modification de schéma ou de statistiques).

**Activation de la correction automatique du choix de plan**


Vous pouvez activer le réglage automatique pour chaque base de données et spécifier que le dernier bon plan connu doit être forcé quand une régression de changement de plan est détectée. Pour cela, utilisez la commande suivante :

```
ALTER DATABASE current
SET AUTOMATIC_TUNING ( FORCE_LAST_GOOD_PLAN = ON );
```
Une fois que vous avez activé cette option, ..!NCLUDE-NotShown--ssde_md--../../includes/ssde_md.md)] force automatiquement les recommandations applicables si le gain d’UC estimé est supérieur à 10 secondes ou si le nombre d’erreurs dans le nouveau plan est supérieur au nombre d’erreurs dans le plan recommandé, puis vérifie que le plan forcé est préférable au plan actuel.

**Autre possibilité : la correction manuelle du choix de plan**


Quand le réglage automatique n’est pas activé, les utilisateurs doivent régulièrement surveiller le système et rechercher les requêtes régressées. Quand un plan régressé est utilisé, ils doivent rechercher un bon plan connu et forcer son utilisation à la place du plan actuel à l’aide de la procédure sp_query_store_force_plan.







## <a name="similar-articles"></a>Articles similaires

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

Cette section liste les articles très similaires récemment mis à jour dans d’autres domaines, dans notre dépôt public GitHub.com : [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Domaines avec des articles nouveaux ou mis à jour récemment

- [Nouveaux + Mis à jour (3 + 12) : **Analytique avancée pour SQL** (documentation)](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nouveaux + Mis à jour (5 + 0) : **Se connecter à SQL** (documentation)](../connect/new-updated-connect.md)
- [Nouveaux + Mis à jour (5 + 1) : **Moteur de base de données pour SQL** (documentation)](../database-engine/new-updated-database-engine.md)
- [Nouveaux + Mis à jour (19 + 82) : **Integration Services pour SQL** (documentation)](../integration-services/new-updated-integration-services.md)
- [Nouveaux + Mis à jour (1 + 8) : **Linux pour SQL** (documentation)](../linux/new-updated-linux.md)
- [Nouveaux + Mis à jour (12 + 1) : **Bases de données relationnelles pour SQL** (documentation)](../relational-databases/new-updated-relational-databases.md)
- [Nouveaux + Mis à jour (0 + 1) : **Reporting Services pour SQL** (documentation)](../reporting-services/new-updated-reporting-services.md)
- [Nouveaux + Mis à jour (7 + 1) : **Microsoft SQL Server** (documentation)](../sql-server/new-updated-sql-server.md)
- [Nouveaux + Mis à jour (1 + 1) : **SQL Server Data Tools (SSDT)** (documentation)](../ssdt/new-updated-ssdt.md)
- [Nouveaux + Mis à jour (0 + 2) : **SQL Server Migration Assistant (SSMA)** (documentation)](../ssma/new-updated-ssma.md)
- [Nouveaux + Mis à jour (1 + 4) : **SQL Server Management Studio (SSMS)** (documentation)](../ssms/new-updated-ssms.md)
- [Nouveaux + Mis à jour (4 + 1) : **Transact-SQL** (documentation)](../t-sql/new-updated-t-sql.md)
- [Nouveaux + Mis à jour (0 + 1) : **Outils pour SQL** (documentation)](../tools/new-updated-tools.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Domaines sans article nouveau ou mis à jour récemment

- [Nouveaux + Mis à jour (0 + 0) : **ActiveX Data Objects (ADO) pour SQL** (documentation)](../ado/new-updated-ado.md)
- [Nouveaux + Mis à jour (0 + 0) : **Analysis Services pour SQL** (documentation)](../analysis-services/new-updated-analysis-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Data Quality Services pour SQL** (documentation)](../data-quality-services/new-updated-data-quality-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Extensions DMX (Data Mining Extensions) pour SQL** (documentation)](../dmx/new-updated-dmx.md)
- [Nouveaux + Mis à jour (0 + 0) : **Master Data Services (MDS) for SQL** (documentation)](../master-data-services/new-updated-master-data-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Expressions MDX (Multidimensional Expressions) pour SQL** (documentation)](../mdx/new-updated-mdx.md)
- [Nouveaux + Mis à jour (0 + 0) : **ODBC (Open Database Connectivity) pour SQL** (documentation)](../odbc/new-updated-odbc.md)
- [Nouveaux + Mis à jour (0 + 0) : **PowerShell pour SQL** (documentation)](../powershell/new-updated-powershell.md)
- [Nouveaux + Mis à jour (0 + 0) : **Exemples pour SQL** (documentation)](../sample/new-updated-sample.md)
- [Nouveaux + Mis à jour (0 + 0) : **XQuery pour SQL** (documentation)](../xquery/new-updated-xquery.md)




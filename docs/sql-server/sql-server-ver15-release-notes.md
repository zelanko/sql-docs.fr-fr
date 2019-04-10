---
title: Notes de publication de SQL Server 2019 | Microsoft Docs
ms.date: 03/27/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: release-landing
ms.topic: article
ms.assetid: 13942af8-5a40-4cef-80f5-918386767a47
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: = sql-server-ver15 || = sqlallproducts-allversions
ms.openlocfilehash: 62c637f8432fd168a9b23a92b7d50c00ea6c1e14
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860060"
---
# <a name="sql-server-2019-preview-release-notes"></a>Notes de publication de SQL Server 2019 Preview
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article décrit les limitations et problèmes connus concernant les versions [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] Community Technology Preview (CTP). Pour des informations connexes, consultez :
- [Nouveautés de SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md)

> [!NOTE]
> Les préversions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sont mises à votre disposition pour que vous puissiez découvrir les fonctionnalités de la version à venir. Elles ne sont pas prises en charge ou distribuées sous licence dans le cadre d’une utilisation en production. Les scénarios suivants sont explicitement non pris en charge :
>
> - Installation côte à côte avec d’autres versions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]
> - Mise à niveau d’une instance existante de SQL Server à partir de n’importe quelle version

**Essayez [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] !**
- [![Télécharger à partir du Centre d’évaluation](../includes/media/download2.png)](https://go.microsoft.com/fwlink/?LinkID=862101) [Télécharger [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] en vue de l’installer sur Windows](https://go.microsoft.com/fwlink/?LinkID=862101)
- Installer sur Linux pour [Red Hat Enterprise Server](../linux/quickstart-install-connect-red-hat.md), [SUSE Linux Enterprise Server](../linux/quickstart-install-connect-suse.md) et [Ubuntu](../linux/quickstart-install-connect-ubuntu.md).
- [Exécuter SQL Server 2019 sur Docker](../linux/quickstart-install-connect-docker.md).

## <a name="ctp-24"></a>CTP 2.4
[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.4 est la dernière version publique de [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)].

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.4 est disponible uniquement en version d’évaluation. Aucune autre édition n’est disponible. La prise en charge des versions CTP est décrite dans le fichier `license_Eval.rtf` qui se trouve sur votre support d’installation.

Une prise en charge limitée peut être disponible aux emplacements suivants :

- Forums
  - [Commentaires sur SQL Server](https://aka.ms/sqlfeedback)
  - [Bien démarrer avec SQL Server](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=sqlgetstarted)
  - [Transact-SQL](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=transactsql)
  - [Documentation SQL Server](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=sqldocumentation)

- Ou tweetez [@SQLServer](https://twitter.com/SQLServer) avec [#sqlhelp](https://twitter.com/search?q=%23sqlhelp)

### <a name="documentation-ctp-24"></a>Documentation (CTP 2.4)

- **Problème et impact sur le client** : la documentation pour SQL Server 2019 (15.x) est limitée, et le contenu est inclus avec l’ensemble de documentation [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Dans les articles, le contenu propre à SQL Server 2019 (15.x) est noté avec **S’applique à**.

- **Problème et impact sur le client** : la documentation [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] peut être filtrée par version. Utilisez le contrôle en haut à gauche de chaque page de documentation pour filtrer selon vos besoins.

- **Problème et impact sur le client** : aucun contenu hors connexion n’est disponible pour SQL Server 2019 (15.x).

### <a name="hardware-and-software-requirements-ctp-24"></a>Configuration matérielle et logicielle requise (CTP 2.4)

- **Problème et impact sur le client** : la configuration matérielle et logicielle requise est en cours d’examen et n’est pas finalisée pour la sortie du produit.

  - **Matériel**
    - [Windows : processeur, mémoire et système d’exploitation requis](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md#pmosr)
    - [Linux : configuration requise](../linux/sql-server-linux-setup.md#system)
  - **Logiciel**
    - Windows Server 2016 ou version ultérieure. Pour connaître la configuration requise supplémentaire, consultez [Configuration requise pour l’installation de SQL Server](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).
    - Microsoft .NET Framework 4.6.2. Disponible sur le [Centre de téléchargement](https://www.microsoft.com/download/details.aspx?id=53344).
    - Pour Linux, reportez-vous à [Linux : plateformes prises en charge](../linux/sql-server-linux-setup.md#supportedplatforms).

### <a name="updated-compiler"></a>Compilateur mis à jour

- **Problème et impact sur le client** : [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] est construit avec un compilateur mis à jour. CTP 2.1 disposait d’une erreur connue où les résultats de scénarios de conversion ou à virgule flottante retournaient une valeur différente des versions précédentes à cause du compilateur mis à jour. CTP 2.2 inclut une solution qui veille à ce que les scénarios concernés retournent les mêmes résultats que les versions précédentes de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. À compter de la version CTP 2.3, nous n’avons connaissance d’aucun problème. Veuillez signaler toute anomalie de résultat comparé à [!INCLUDE[ss2017](../includes/sssqlv14-md.md)] à l’équipe [[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]](http://aka.ms/sqlfeedback) sans tarder.

- **Solution de contournement**: Néant

- **S’applique à** : SQL Server 2019 CTP 2.4, CTP 2.3, CTP 2.2, CTP 2.1

### <a name="utf-8-collations"></a>Classements UTF-8

- **Problème et impact sur le client** : les classements prenant en charge UTF-8 ne peuvent pas être utilisés avec certaines fonctionnalités [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. UTF-8 n’est pas pris en charge quand les fonctionnalités [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] suivantes sont en cours d’utilisation :

  - Serveur lié
  - OLTP en mémoire
  - Table externe pour PolyBase
  - Always Encrypted

  > [!Note]
  > Actuellement, l’interface utilisateur d’Azure Data Studio et de SQL Server Data Tools (SSDT) ne permet pas de choisir des classements prenant en charge UTF-8. Il en va différemment de l’interface utilisateur de la dernière version [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] de SSMS.
 
- **Solution de contournement**: aucune pour [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP (toutes versions).

- **S’applique à** : [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.4, CTP 2.3, CTP 2.2, CTP 2.1, CTP 2.0.

### <a name="sql-graph"></a>Graph SQL

- **Problème et impact sur le client** : les outils qui ont des dépendances vis-à-vis de DACFx comme l’importation ou l’exportation ne fonctionnent pas pour les nouvelles fonctionnalités de graphe : les contraintes d’arête ou la syntaxe DML de fusion. L’écriture de scripts dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] peut ne pas fonctionner.

- **Solution de contournement**: l’écriture de scripts [!INCLUDE[tsql](../includes/tsql-md.md)] et leur exécution sur le serveur à l’aide de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ou SQLCMD fonctionnent. L’exportation ou l’importation d’objets de base de données qui créent des contraintes d’arête, ont la nouvelle syntaxe DML de fusion ou créent des tables dérivées/vues sur des objets de graphe ne fonctionnent pas. Les utilisateurs doivent créer manuellement ces objets dans leur base de données à l’aide de scripts [!INCLUDE[tsql](../includes/tsql-md.md)]. 

- **S’applique à** : [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.4, CTP 2.3, CTP 2.2, CTP 2.1, 2.0.

### <a name="always-encrypted-with-secure-enclaves"></a>Always Encrypted avec enclaves sécurisées

- **Problème et impact sur le client** : les calculs avancés sont en attente de plusieurs optimisations des performances incluent des fonctionnalités limitées (aucune indexation, etc.) et sont actuellement désactivés par défaut.

- **Solution de contournement**: pour activer les calculs avancés, exécutez `DBCC traceon(127,-1)`. Pour plus d’informations, consultez [Activer les calculs avancés](../relational-databases/security/encryption/configure-always-encrypted-enclaves.md#configure-a-secure-enclave).

- **S’applique à** : [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.4, CTP 2.3, 2.2, CTP 2.1, 2.0.

### <a name="system-dynamic-management-views"></a>Vues de gestion dynamique système

- **Problème et impact sur le client** : La fonction table système [sys.dm_db_objects_disabled_on_compatibility_level_change](../relational-databases/system-dynamic-management-views/spatial-data-sys-dm-db-objects-disabled-on-compatibility-level-change.md) retourne des valeurs aléatoires dans la colonne `dependency`.

- **S’applique à** : [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.4, CTP 2.3.

[!INCLUDE[get-help-options-msft-only](../includes/paragraph-content/get-help-options.md)]

![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)

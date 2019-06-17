---
title: Notes de publication de SQL Server 2019 | Microsoft Docs
ms.date: 05/22/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: release-landing
ms.topic: article
ms.assetid: 13942af8-5a40-4cef-80f5-918386767a47
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: = sql-server-ver15 || = sqlallproducts-allversions
ms.openlocfilehash: 8f44927fb59e6d1b613b2a67e26aed980b3a080a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65993942"
---
# <a name="sql-server-2019-preview-release-notes"></a>Notes de publication de SQL Server 2019 Preview
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article décrit les limitations et problèmes connus concernant les versions [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] Community Technology Preview (CTP). Pour des informations connexes, consultez :
- [Nouveautés de SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md)

## <a name="ctp-30"></a>CTP 3.0

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 3.0 est la dernière version publique de [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)].

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 3.0 est disponible uniquement en édition d’évaluation. Aucune autre édition n’est disponible. 

Vous trouverez les détails complets de la prise en charge et de la gestion des licences pour les versions CTP dans `license_Eval.rtf` sur votre support d’installation.

[!INCLUDE[ctp-support-exclusion](../includes/ctp-support-exclusion.md)]

## <a name="documentation"></a>Documentation

- **Problème et impact sur le client** : la documentation pour SQL Server 2019 (15.x) est limitée, et le contenu est inclus avec l’ensemble de documentation [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Dans les articles, le contenu propre à SQL Server 2019 (15.x) est noté avec **S’applique à**.

- **Problème et impact sur le client** : la documentation [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] peut être filtrée par version. Utilisez le contrôle en haut à gauche de chaque page de documentation pour filtrer selon vos besoins.

- **Problème et impact sur le client** : aucun contenu hors connexion n’est disponible pour SQL Server 2019 (15.x).

## <a name="hardware-and-software-requirements"></a>Configuration matérielle et logicielle requise

- **Problème et impact sur le client** : la configuration matérielle et logicielle requise est en cours d’examen et n’est pas finalisée pour la sortie du produit.

  - **Matériel**
    - [Windows : processeur, mémoire et système d’exploitation requis](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md#pmosr)
    - [Linux : configuration système requise](../linux/sql-server-linux-setup.md#system)
  - **Logiciels**
    - Windows Server 2016 ou version ultérieure. Pour connaître la configuration requise supplémentaire, consultez [Configuration requise pour l’installation de SQL Server](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).
    - Microsoft .NET Framework 4.6.2. Disponible sur le [Centre de téléchargement](https://www.microsoft.com/download/details.aspx?id=53344).
    - Pour Linux, reportez-vous à [Linux : plateformes prises en charge](../linux/sql-server-linux-setup.md#supportedplatforms).

## <a name = "release-notes"></a>Fonctionnalités exclues de la prise en charge

- **Problème et impact sur le client**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] exclut la prise en charge des composants, fonctionnalités et scénarios suivants :
  - SQL Sever Analysis Services
  - SQL Server Reporting Services
  - Groupes de disponibilité AlwaysOn sur Kubernetes
  - Récupération de base de données accélérée
  - Métadonnées tempdb à mémoire optimisée

- **Solution de contournement**: Aucun. L’exclusion s’applique à tous les clients, y compris aux participants au programme d’adoption anticipée de SQL.

- **S’applique à** : CTP 3.0

## <a name="updated-compiler"></a>Compilateur mis à jour

- **Problème et impact sur le client** : [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] est construit avec un compilateur mis à jour. CTP 2.1 disposait d’une erreur connue où les résultats de scénarios de conversion ou à virgule flottante retournaient une valeur différente des versions précédentes à cause du compilateur mis à jour. CTP 2.2 inclut une solution qui veille à ce que les scénarios concernés retournent les mêmes résultats que les versions précédentes de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. À compter de la version CTP 3.0, nous n’avons connaissance d’aucun problème. Veuillez signaler toute anomalie de résultat comparé à [!INCLUDE[ss2017](../includes/sssqlv14-md.md)] à l’équipe [[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]](http://aka.ms/sqlfeedback) sans tarder.

- **Solution de contournement**: Néant

- **S’applique à** : SQL Server 2019 CTP 3.0, CTP 2.5, CTP 2.4, CTP 2.3, CTP 2.2, CTP 2.1

## <a name="installation-wizard-may-wait-between-eula-pages"></a>L’Assistant Installation peut attendre entre les pages du CLUF

- **Problème et impact sur le client** : pendant l’installation avec l’Assistant Installation, le processus peut attendre une quantité excessive de temps entre le contrat de licence utilisateur final (CLUF) pour R Services et le CLUF pour Python.

- **Solution de contournement**: attendez que l’Assistant Installation continue. Le délai d’attente peut dépasser 30 minutes.

- **S’applique à** : SQL Server 2019 CTP 3.0

## <a name="utf-8-collations"></a>Classements UTF-8

- **Problème et impact sur le client** : les classements prenant en charge UTF-8 ne peuvent pas être utilisés avec certaines fonctionnalités [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. UTF-8 n’est pas pris en charge quand les fonctionnalités [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] suivantes sont en cours d’utilisation :

  - OLTP en mémoire
  - Table externe pour PolyBase
  - Always Encrypted

  > [!Note]
  > Actuellement, l’interface utilisateur d’Azure Data Studio et de SQL Server Data Tools (SSDT) ne permet pas de choisir des classements prenant en charge UTF-8. Il en va différemment de l’interface utilisateur de la dernière version 18 de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] SSMS.
 
- **Solution de contournement**: aucune pour [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP (toutes versions).

- **S’applique à** : [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 3.0, CTP 2.5, CTP 2.4, CTP 2.3, CTP 2.2, CTP 2.1, CTP 2.0.

## <a name="always-encrypted-with-secure-enclaves"></a>Always Encrypted avec enclaves sécurisées

- **Problème et impact sur le client** : les calculs avancés sont en attente de plusieurs optimisations des performances incluent des fonctionnalités limitées (aucune indexation, etc.) et sont actuellement désactivés par défaut.

- **Solution de contournement**: pour activer les calculs avancés, exécutez `DBCC traceon(127,-1)`. Pour plus d’informations, consultez [Activer les calculs avancés](../relational-databases/security/encryption/configure-always-encrypted-enclaves.md#configure-a-secure-enclave).

- **S’applique à** : [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 3.0, CTP 2.5, CTP 2.4, CTP 2.3, 2.2, CTP 2.1, 2.0.

[!INCLUDE[get-help-options-msft-only](../includes/paragraph-content/get-help-options.md)]

![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)

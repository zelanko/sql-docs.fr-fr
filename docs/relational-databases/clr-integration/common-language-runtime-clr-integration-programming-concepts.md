---
title: Programmation CLR (Common Language Runtime)
description: Liens vers des Articles de programmation CLR (Common Language Runtime)
ms.custom: seo-lt-2019
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- CLR [SQL Server] See common language runtime [SQL Server]
- Database Engine [SQL Server], .NET Framework
- .NET Framework [SQL Server], Database Engine programming
- common language runtime [SQL Server]
- .NET Framework [SQL Server]
ms.assetid: 951bf851-3e6e-4361-ae6a-2bcd5b837ebd
author: rothja
ms.author: jroth
ms.openlocfilehash: c314745122f0735b2b26ac2bb021f20f637b2a28
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75256192"
---
# <a name="common-language-runtime-clr-integration-programming-concepts"></a>Concepts de programmation pour l'intégration du CLR
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Depuis [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] propose désormais l'intégration du composant CLR (Common Language Runtime) du .NET Framework pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Cela signifie que vous pouvez désormais écrire des procédures stockées, des déclencheurs, des types définis par l'utilisateur, des fonctions définies par l'utilisateur, des agrégats définis par l'utilisateur et des fonctions table d'accès en continu, à l'aide de n'importe quel langage du .NET Framework, notamment [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET et [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#.  
  
 L'espace de noms Microsoft.SqlServer.Server inclut les fonctionnalités principales relatives à la programmation CLR dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Toutefois, l'espace de noms Microsoft.SqlServer.Server est documenté dans le Kit de développement logiciel (SDK) du .NET Framework. Cette documentation n'est pas incluse dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Par défaut, le .NET Framework est installé avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], alors que le Kit de développement .NET Framework SDK ne l'est pas. Si le Kit de développement .NET Framework SDK n'est pas installé sur votre ordinateur et inclus dans l'ensemble de la documentation en ligne, les liens vers son contenu dans cette section ne fonctionnent pas. Installez le Kit de développement .NET Framework SDK. Une fois installé, ajoutez le kit de développement logiciel (SDK) au regroupement et à la table des matières de la documentation en suivant les instructions fournies dans [installation du kit de développement logiciel (SDK) .NET Framework](https://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx).  
  
> [!NOTE]  
>  Les fonctionnalités CLR, telles que les fonctions utilisateur CLR, ne sont *pas* prises en charge pour les Azure SQL Database.  
  
 Le tableau suivant décrit les rubriques de cette section.  
  
 [Vue d’ensemble de l’intégration du Common Language Runtime &#40;CLR&#41;](../../relational-databases/clr-integration/common-language-runtime-integration-overview.md)  
 Fournit une brève vue d'ensemble du CLR et explique comment et pourquoi cette technologie a été utilisée dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Décrit les avantages liés à l'utilisation du CLR pour créer des objets de base de données.  
  
 [Assemblys &#40;Moteur de base de données&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md)  
 Décrit l'utilisation d'assemblys dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin de déployer des fonctions, des procédures stockées, des déclencheurs, des agrégats définis par l'utilisateur et des types définis par l'utilisateur écrits dans l'un des langages de code managé hébergés par le CLR (Common Language Runtime) [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework, et non écrits en [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 [Génération d’objets de base de données avec Common Language Runtime &#40;l’intégration du CLR&#41;](../../relational-databases/clr-integration/database-objects/building-database-objects-with-common-language-runtime-clr-integration.md)  
 Décrit les types d'objets qui peuvent être créés à l'aide du CLR et examine les spécifications requises pour générer des objets de base de données CLR.  
  
 [Accès aux données à partir d'objets de base de données CLR](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md)  
 Explique comment une routine CLR peut accéder aux données stockées dans une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Sécurité de l'intégration du CLR](../../relational-databases/clr-integration/security/clr-integration-security.md)  
 Décrit le modèle de sécurité de l'intégration du CLR.  
  
 [Débogage d'objets de base de données CLR](../../relational-databases/clr-integration/debugging-clr-database-objects.md)  
 Décrit les limitations et les exigences relatives au débogage des objets de base de données CLR.  
  
 [Déploiement d'objets de base de données CLR](../../relational-databases/clr-integration/deploying-clr-database-objects.md)  
 Décrit le déploiement des assemblys sur les serveurs de production.  
  
 [Gestion des assemblys d’intégration du CLR](../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)  
 Explique comment créer et supprimer des assemblys d'intégration du CLR.  
  
 [Surveillance et dépannage des objets de base de données managés](../../relational-databases/clr-integration/monitoring-and-troubleshooting-managed-database-objects.md)  
 Fournit des informations sur les outils à l'aide desquels vous pouvez surveiller et dépanner les objets de base de données et les assemblys managés s'exécutant dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Scénarios d’utilisation et exemples pour le Common Language Runtime &#40;l’intégration du CLR&#41;](https://msdn.microsoft.com/library/33aac25f-abb4-4f29-af88-4a0dacd80ae7)  
 Décrit des scénarios d'usage et des exemples de code à l'aide d'objets CLR.  
  
## <a name="see-also"></a>Voir aussi  
 [Assemblys &#40;Moteur de base de données&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md)   
 [Installation du SDK .NET Framework](https://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx)  
  
  

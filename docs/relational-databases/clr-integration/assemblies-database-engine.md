---
title: Assemblages (moteur de base de données) Microsoft Docs
description: Une instance SQL Server peut héberger des assemblages qui déploient des fonctions, des procédures, des déclencheurs et des agrégats et types définis par l’utilisateur écrits dans un langage CLR.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration]
- assemblies [CLR integration], about assemblies
- managed code [SQL Server], assemblies
ms.assetid: 4b146437-3061-47f6-9e8c-26eeea10b54e
author: rothja
ms.author: jroth
ms.openlocfilehash: 386e1980ae19ba4f98222b51a4955b024f815083
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488072"
---
# <a name="assemblies-database-engine"></a>Assemblys (moteur de base de données)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Toutes les rubriques de cette section vous aident à mieux comprendre, concevoir et mettre en œuvre les assemblys.  
  
 Les assemblages sont des fichiers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DLL utilisés dans le cas de déploiement de fonctions, de procédures stockées, de déclencheurs, d’agrégats définis par l’utilisateur et de types définis par l’utilisateur qui sont écrits dans l’une des langues de code gérées hébergées par l’heure courante de fonctionnement de la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] langue (CLR), au lieu de . [!INCLUDE[tsql](../../includes/tsql-md.md)]  
  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], un assembly est un objet qui fait référence à un module d'applications managées (fichier .dll) qui a été créé dans le Common Language Runtime (CLR) [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Un assembly contient des métadonnées de classe et du code managé. Le téléchargement d'un assembly dans une instance SQL Server constitue la première étape nécessaire à la création des objets de base de données suivants :  
  
-   Fonctions CLR. Pour plus d’informations, voir [Créer des fonctions CLR](../../relational-databases/user-defined-functions/create-clr-functions.md).  
  
-   Procédures stockées CLR. Pour plus d’informations, voir [CLR Stored Procedures](https://msdn.microsoft.com/library/bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33).  
  
-   Déclencheurs CLR. Pour plus d’informations, voir [Create CLR Triggers](../../relational-databases/triggers/create-clr-triggers.md).  
  
-   Fonctions d'agrégation définies par l'utilisateur. Pour plus d’informations, voir [Créer des agrégats définis par l’utilisateur](../../relational-databases/user-defined-functions/create-user-defined-aggregates.md).  
  
-   Types définis par l'utilisateur. Pour plus d’informations, consultez [Types CLR définis par l’utilisateur](../../relational-databases/native-client/features/using-user-defined-types.md).  
  
 Les assemblys sont chargés des fonctions suivantes dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   Contenir le code managé qui exécute la fonctionnalité d'un ou de plusieurs objets de données CLR mentionnés précédemment.  
  
-   Contenir les métadonnées décrivant le numéro de version et la culture de l'assembly, une clé publique facultative qui identifie de manière unique la liste des classes de l'assembly, les méthodes définies dans l'assembly et l'architecture de processeur de l'assembly.  
  
-   Gérer le niveau d'accès du code managé aux ressources extérieures en régulant les autorisations d'accès au code.  
  
-   Contenir les métadonnées relatives aux dépendances avec les autres assemblys auxquelles fait référence l'assembly.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Conception d'assemblys](../../relational-databases/clr-integration/assemblies-designing.md)|Explique les points à prendre en considération avant la création d'un assembly, notamment : assemblys à inclure, autorisations d'accès au code et autres restrictions.|  
|[Implémentation d'assemblys](../../relational-databases/clr-integration/assemblies-implementing.md)|Explique comment créer et supprimer des assemblys, comment et quand modifier des assemblys et comment récupérer les métadonnées relatives aux assemblys.|  
|[Obtention d'informations sur les assemblys](../../relational-databases/clr-integration/assemblies-getting-information.md)|Répertorie les affichages catalogue et les fonctions qu'il est possible d'interroger pour récupérer les métadonnées relatives aux assemblys.|  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts de programmation pour l’intégration du CLR &#40;Common Language Runtime&#41;](../../relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
  
  

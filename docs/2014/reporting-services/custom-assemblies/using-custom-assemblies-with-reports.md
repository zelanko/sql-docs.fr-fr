---
title: Utilisation d’assemblages personnalisés avec des rapports | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom assemblies [Reporting Services]
- assemblies [Reporting Services], custom
- custom assemblies [Reporting Services], about custom assemblies
ms.assetid: 53d141d0-2185-466a-84dc-7b90d284da3d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e79f48f4e4a2eb5fbc83c353461709658caf2509
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63265657"
---
# <a name="using-custom-assemblies-with-reports"></a>Utilisation d'assemblys personnalisés avec des rapports
  Dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vous pouvez écrire du code personnalisé pour les valeurs, les styles et la mise en forme des éléments de rapport. Par exemple, vous pouvez utiliser du code personnalisé pour mettre en forme les devises en fonction de paramètres régionaux, marquer certaines valeurs avec une mise en forme spéciale ou appliquer d'autres règles d'entreprise en pratique dans votre société. Une façon d’inclure ce code dans vos rapports consiste à créer un assembly de code personnalisé [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] à l’aide du que vous pouvez référencer à partir de vos fichiers de définition de rapport. Le serveur appelle les fonctions de votre assembly personnalisé lors de l'exécution d'un rapport. Les assemblys personnalisés peuvent être utilisés pour extraire des fonctions spéciales que vous envisagez d'utiliser dans vos rapports.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Référencement d'assemblys dans un Fichier RDL](referencing-assemblies-in-an-rdl-file.md)  
 Décrit comment référencer vos assemblys personnalisés dans un fichier RDL (Report Definition Language File).  
  
 [Déploiement d'un assembly personnalisé](deploying-a-custom-assembly.md)  
 Décrit comment déployer un assembly personnalisé sur le Concepteur de rapports et le serveur de rapports.  
  
 [Utilisation d'assemblys personnalisés avec noms forts](using-strong-named-custom-assemblies.md)  
 Décrit comment utiliser des assemblys personnalisés avec des noms forts.  
  
 [Déclaration d'autorisations dans les assemblys personnalisés](asserting-permissions-in-custom-assemblies.md)  
 Décrit comment déployer des assemblys personnalisés avec des autorisations limitées et spécifiques, et comment déclarer ces autorisations dans le code.  
  
 [Accès aux assemblys personnalisés par le biais d'expressions](accessing-custom-assemblies-through-expressions.md)  
 Décrit comment appeler des méthodes d'assembly personnalisé sous la forme d'expressions de rapport dans vos définitions de rapport.  
  
 [Initialisation d'objets Assembly personnalisés](initializing-custom-assembly-objects.md)  
 Décrit comment initialiser les valeurs des objets d'assembly personnalisé appelés à partir d'un rapport.  
  
 [Procédure : Déboguer des assemblages personnalisés](how-to-debug-custom-assemblies.md)  
 Décrit comment déboguer le code de votre assembly personnalisé.  
  
## <a name="see-also"></a>Voir aussi  
 [RDL (Report Definition Language) &#40;SSRS&#41;](../reports/report-definition-language-ssrs.md)  
  
  

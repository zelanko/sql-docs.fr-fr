---
title: Paramètres de Integration Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, parameters
ms.assetid: b1bb3ea3-8097-4e76-b9c2-78a0f46a23bc
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 100e796bb27d1e60db000a364a0432273dd5cafb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66094237"
---
# <a name="integration-services-parameters"></a>Paramètres Integration Services
  Pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vous pouvez décider d’analyser [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] des packages sur l’ordinateur ou [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] des fichiers de package dans le système de fichiers. Si vous analysez des fichiers dans le système de fichiers, fournissez un chemin d'accès au dossier qui contient les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="options"></a>Options  
 **Analyser les packages SSIS sur l'ordinateur**  
 Sélectionnez cette option pour analyser les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur l'ordinateur. Cette option est sélectionnée par défaut.  
  
 **Analyser les fichiers de package SSIS**  
 Sélectionnez cette option pour analyser les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dans le système de fichiers.  
  
 **Chemin d'accès aux packages SSIS**  
 Recherchez un chemin UNC ou un chemin local qui contient vos packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Il est inutile d'inclure les noms de fichiers. Si le chemin d’accès que vous avez entré est inaccessible, vous ne pouvez pas cliquer sur **suivant**. Par défaut, le chemin d’accès est vide. Ce champ est activé uniquement lorsque vous sélectionnez **analyser les fichiers de package SSIS**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du conseiller de mise à niveau](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Guide de référence de l'interface utilisateur du Conseiller de mise à niveau](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  

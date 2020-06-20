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
ms.openlocfilehash: 76a5ebe7018fdc58f02a4d2454d40f172c752c4e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059268"
---
# <a name="integration-services-parameters"></a>Paramètres Integration Services
  Pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , vous pouvez décider d’analyser [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] des packages sur l’ordinateur ou des [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] fichiers de package dans le système de fichiers. Si vous analysez des fichiers dans le système de fichiers, fournissez un chemin d'accès au dossier qui contient les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="options"></a>Options  
 **Analyser les packages SSIS sur l'ordinateur**  
 Sélectionnez cette option pour analyser les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur l'ordinateur. Cette option est activée par défaut.  
  
 **Analyser les fichiers de package SSIS**  
 Sélectionnez cette option pour analyser les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dans le système de fichiers.  
  
 **Chemin d'accès aux packages SSIS**  
 Recherchez un chemin UNC ou un chemin local qui contient vos packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Il est inutile d'inclure les noms de fichiers. Si le chemin d’accès que vous avez entré est inaccessible, vous ne pouvez pas cliquer sur **suivant**. Par défaut, le chemin d’accès est vide. Ce champ est activé uniquement lorsque vous sélectionnez **analyser les fichiers de package SSIS**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du conseiller de mise à niveau](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Guide de référence de l'interface utilisateur du Conseiller de mise à niveau](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  

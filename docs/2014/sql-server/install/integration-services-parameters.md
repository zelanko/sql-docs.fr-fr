---
title: Paramètres Integration Services | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Integration Services, parameters
ms.assetid: b1bb3ea3-8097-4e76-b9c2-78a0f46a23bc
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f178c02cc93d23a14e0fb658398e5f0ba4cf6dc0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043745"
---
# <a name="integration-services-parameters"></a>Paramètres Integration Services
  Pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vous pouvez décider d’analyser [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages sur l’ordinateur, ou [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] les fichiers de package dans le système de fichiers. Si vous analysez des fichiers dans le système de fichiers, fournissez un chemin d'accès au dossier qui contient les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="options"></a>Options  
 **Analyser les packages SSIS sur l’ordinateur**  
 Sélectionnez cette option pour analyser les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur l'ordinateur. Cette option est sélectionnée par défaut.  
  
 **Analyser les fichiers de package SSIS**  
 Sélectionnez cette option pour analyser les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dans le système de fichiers.  
  
 **Chemin d’accès aux packages SSIS**  
 Recherchez un chemin UNC ou un chemin local qui contient vos packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Il est inutile d'inclure les noms de fichiers. Si le chemin d’accès que vous avez entrées ne sont pas accessibles, vous ne pouvez pas cliquer **suivant**. Par défaut, le chemin d’accès est vide. Ce champ est activé uniquement lorsque vous sélectionnez **SSIS d’analyser les fichiers de package**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation avec le Conseiller de mise à niveau](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Référence de l’Interface utilisateur Conseiller de mise à niveau](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
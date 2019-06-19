---
title: Masquer les objets système dans l’Explorateur d’objets | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- hiding system objects
- system objects [SQL Server]
- objects [SQL Server], hiding
- Object Explorer, hiding objects
ms.assetid: c01d8804-838c-4f75-b78c-80e41e4fffdc
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 5b36198aba754f8424e29ba529fe936516213cad
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65102926"
---
# <a name="hide-system-objects-in-object-explorer"></a>Masquer les objets système dans l’Explorateur d’objets
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Cette rubrique explique comment masquer les objets système dans l'Explorateur d'objets dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Le nœud **Bases de données** de l’Explorateur d’objets contient des objets système tels que les bases de données système. Utilisez les pages **Outils**/**Options** pour masquer les objets système. Certains objets système, tels que les fonctions système et les types de données système, ne sont pas affectés par ce paramètre.  
  
## <a name="SSMSProcedure"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-hide-system-objects-in-object-explorer"></a>Pour masquer les objets système dans l'Explorateur d'objets  
  
1.  Dans le menu **Outils** , cliquez sur **Options**.  
  
2.  Dans la page **Environnement/Démarrage** , sélectionnez **Masquer les objets système dans l’Explorateur d’objets**, puis cliquez sur **OK**.  
  
3.  Dans la boîte de dialogue **SQL Server Management Studio** , cliquez sur **OK** pour que SQL Server Management Studio redémarre et que la modification prenne effet.  
  
4.  Fermez et rouvrez SQL Server Management Studio.  
  

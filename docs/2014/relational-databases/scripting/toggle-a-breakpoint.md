---
title: Basculer un point d’arrêt | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c477ab89-a1cd-4f2c-aa7c-40525041100f
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6a04f258a7f92c38f560eb0ecc68e7a24e37597a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37315609"
---
# <a name="toggle-a-breakpoint"></a>Basculer un point d'arrêt
  Le fait de définir un point d'arrêt sur une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] s'appelle le basculement d'un point d'arrêt.  
  
## <a name="breakpoints"></a>Points d'arrêt  
 Une fois le point d'arrêt défini, il est représenté par une icône dans la barre grise à gauche de l'instruction. Cette icône s'appelle un glyphe de point d'arrêt. [!INCLUDE[tsql](../../includes/tsql-md.md)] Les points d’arrêt sont appliqués à une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] complète. Lorsqu'un point d'arrêt est activé, le débogueur met en surbrillance l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] associée.  
  
 S'il existe plusieurs instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] sur une ligne, vous pouvez basculer un point d'arrêt pour chaque instruction. Cliquer dans la barre grise à gauche de la fenêtre bascule un point d'arrêt sur la première instruction de la ligne. Vous pouvez basculer un point d’arrêt dans une instruction suivante en mettant en surbrillance une partie de l’instruction ou en plaçant le curseur dans l’instruction, puis en appuyant sur F9 ou en cliquant sur **Basculer le point d’arrêt** dans le menu **Déboguer** . Si plusieurs points d'arrêt se trouvent sur une ligne, un seul glyphe de point d'arrêt se trouve dans la barre grise à gauche.  
  
 Une fois qu'un point d'arrêt a été basculé, vous pouvez effectuer plusieurs actions sur celui-ci, par exemple modifier ses propriétés ou les désactiver temporairement. Pour plus d’informations, consultez [Points d’arrêt Transact-SQL](transact-sql-breakpoints.md).  
  
## <a name="toggle-a-breakpoint"></a>Basculer un point d'arrêt  
 **Pour basculer un point d'arrêt sur une instruction Transact-SQL**  
  
1.  Cliquez sur la barre grise à gauche de l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
2.  Vous pouvez également mettre en surbrillance une partie quelconque de l'instruction ou placer le curseur sur l'instruction, puis effectuer l'une des actions suivantes :  
  
    -   Appuyez sur F9.  
  
    -   Dans le menu **Déboguer** , cliquez sur **Basculer le point d’arrêt**.  
  
  

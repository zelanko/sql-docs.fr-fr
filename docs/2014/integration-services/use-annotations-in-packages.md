---
title: Utiliser des annotations dans les packages | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- self-documenting packages
- adding annotations
- annotations [Integration Services]
ms.assetid: 48c8ed9a-b10d-490c-9ba7-4b77aa44e3dd
caps.latest.revision: 40
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ed656e80ae48fb77cbe6c48efe6a38b2810d3a91
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37256705"
---
# <a name="use-annotations-in-packages"></a>Utiliser des annotations dans les packages
  Le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] propose des annotations que vous pouvez utiliser afin de faire en sorte que les packages s'auto-documentent et soient ainsi plus faciles à comprendre et à gérer. Vous pouvez ajouter des annotations au flux de contrôle, au flux de données et aux surfaces de dessin du gestionnaire d'événements du concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] . Les annotations peuvent contenir n'importe quel type de texte et sont utiles pour ajouter des étiquettes, des commentaires et autres informations descriptives à un package. Les annotations sont disponibles uniquement au moment de la conception. Par exemple, elles ne sont pas écrites dans les fichiers journaux.  
  
 Lorsque vous appuyez sur Entrée, le texte est renvoyé à la ligne suivante. La taille de la zone d'annotation augmente automatiquement lorsque vous ajoutez des lignes de texte supplémentaires. Les annotations de package sont conservées en texte clair dans la section CDATA du fichier de package.  
  
 Pour plus d’informations sur les modifications du format du fichier de package, consultez [Format de package SSIS](../../2014/integration-services/ssis-package-format.md).  
  
 Lorsque vous enregistrez le package, le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] enregistre les annotations dans le package.  
  
### <a name="to-add-an-annotation-to-a-package"></a>Pour ajouter une annotation à un package  
  
-   [Ajouter une annotation à un package](../../2014/integration-services/add-an-annotation-to-a-package.md)  
  
  

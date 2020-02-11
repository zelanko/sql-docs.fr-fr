---
title: Programmation de la boîte de message d’exception | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- ExceptionMessageBox class, about ExceptionMessageBox class
- exception message box [SQL Server], about exception message box
- exception message box [SQL Server]
- interfaces [SQL Server]
- exceptions [SQL Server]
- messages [SQL Server], exception message box
ms.assetid: 0b1ba514-6959-4e69-bfd2-3cf3c1ac4b9c
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 205638b82e8d0d71a3d674bd970e4bf8d2e3ea5f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62753372"
---
# <a name="exception-message-box-programming"></a>Programmation de boîte de message d'exception
  La boîte de message d’exception est une interface de programmation installée avec et utilisée [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par les composants graphiques. Il s'agit d'un assembly managé pris en charge que vous pouvez utiliser dans vos applications pour contrôler les messages de manière beaucoup plus rigoureuse et pour donner à vos utilisateurs la possibilité d'enregistrer le contenu des messages d'erreur afin de pouvoir obtenir une assistance ultérieure. La boîte de message d'exception étant installée par toutes les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'exception de [!INCLUDE[ssEW](../../includes/ssew-md.md)], vous pouvez l'utiliser sans configuration supplémentaire sur tout ordinateur sur lequel les composants clients [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ont été installés.  
  
 La classe <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> dans l'espace de noms <xref:Microsoft.SqlServer.MessageBox> a toutes les fonctionnalités de la classe <xref:System.Windows.Forms.MessageBox>, et davantage encore. Idéal pour toutes les tâches pour lesquelles <xref:System.Windows.Forms.MessageBox> peut être utilisé, <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> est conçu pour gérer les exceptions de code managé avec élégance. La boîte de message d'exception vous permet d'effectuer les opérations suivantes :  
  
-   Fournir un texte de bouton personnalisé pour cinq boutons maximum. Les boutons et la boîte de dialogue sont redimensionnés automatiquement en fonction de la longueur du texte.  
  
-   Permettre aux utilisateurs de copier facilement le titre du message, le texte du message, le texte du bouton et les liens d'aide (le cas échant) vers le Presse-papiers ou d'envoyer ces informations dans un message électronique.  
  
-   Affichez toutes les exceptions et les erreurs sous-jacentes dans une arborescence de relations hiérarchiques lorsque les utilisateurs cliquent sur **des informations supplémentaires**.  
  
-   Permettre aux utilisateurs de décider s'il faut afficher le message lorsque la même exception se produit de nouveau.  
  
-   Accéder à un système d'aide en ligne en utilisant un lien d'aide associé à l'exception.  
  
 Pour plus d’informations, consultez [boîte de message d’exception de programme](../../../2014/database-engine/dev-guide/program-exception-message-box.md).  
  
  

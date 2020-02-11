---
title: Développement d’une interface utilisateur pour un énumérateur ForEach personnalisé | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom user interface [Integration Services], custom foreach enumerators
- custom foreach enumerators [Integration Services], developing custom user interface
ms.assetid: 8aa4aa80-c9ba-42b3-ba87-ae5ea5d3cac3
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8965fcda896c67b2ae2e08cde54c679e6504b8b6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62896069"
---
# <a name="developing-a-user-interface-for-a-custom-foreach-enumerator"></a>Développement d'une interface utilisateur pour un énumérateur ForEach personnalisé
  Après avoir remplacé l'implémentation des propriétés et méthodes de la classe de base afin de fournir vos fonctionnalités personnalisées, vous pouvez créer une interface utilisateur personnalisée pour votre énumérateur Foreach. Si vous ne créez pas d'interface utilisateur personnalisée, les utilisateurs peuvent configurer uniquement le nouvel énumérateur Foreach personnalisé en utilisant la fenêtre Propriétés.  
  
 Dans un projet ou assembly d'interface utilisateur personnalisée, vous créez une classe qui implémente l'objet <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI>. Cette classe provient de System.Windows.Forms.UserControl, qui est généralement utilisé pour créer un contrôle composite afin d’héberger d’autres contrôles Windows Forms. Le contrôle que vous créez s’affiche sous l’onglet **Collection** de l’**Éditeur de boucle Foreach**, dans la zone **Configuration de l’énumérateur**.  
  
> [!IMPORTANT]  
>  Après avoir signé et généré votre interface utilisateur personnalisée, puis l’avoir installée dans le Global Assembly Cache comme décrit dans [Génération, déploiement et débogage d’objets personnalisés](../building-deploying-and-debugging-custom-objects.md), n’oubliez pas de fournir le nom complet de cette classe dans la propriété <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute.UITypeName%2A> de la classe<xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>.  
  
## <a name="coding-the-user-interface-control-class"></a>Codage de la classe de contrôle de l'interface utilisateur  
  
### <a name="initializing-the-user-interface"></a>Initialisation de l'interface utilisateur  
 Vous remplacez la méthode <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.Initialize%2A> pour mettre en cache des références à l'objet hôte et aux collections de gestionnaires de connexion et variables définies dans le package.  
  
### <a name="setting-properties-on-the-user-interface-control"></a>Définition de propriétés sur le contrôle de l'interface utilisateur  
 La classe UserControl, de laquelle provient la classe de l’interface utilisateur, est destinée à être utilisée comme contrôle composite afin d’héberger d’autres contrôles Windows Forms. Parce que cette classe héberge d'autres contrôles, vous pouvez concevoir votre interface utilisateur personnalisée en faisant glisser des contrôles, en les réorganisant, en définissant leurs propriétés et en répondant au moment de l'exécution à leurs événements comme dans toute application Windows Forms.  
  
### <a name="saving-settings"></a>Enregistrement des paramètres  
 Vous remplacez la méthode <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.SaveSettings%2A> pour copier les valeurs sélectionnées par l'utilisateur depuis les contrôles vers les propriétés de l'énumérateur lorsque l'utilisateur ferme l'éditeur.  
  
![Icône de Integration Services (petite)](../../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visitez la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un énumérateur Foreach personnalisé](creating-a-custom-foreach-enumerator.md)   
 [Codage d’un énumérateur Foreach personnalisé](coding-a-custom-foreach-enumerator.md)  
  
  

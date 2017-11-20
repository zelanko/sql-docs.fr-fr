---
title: "Développement d’une Interface utilisateur pour un énumérateur ForEach personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-custom-objects
ms.reviewer: 
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom user interface [Integration Services], custom foreach enumerators
- custom foreach enumerators [Integration Services], developing custom user interface
ms.assetid: 8aa4aa80-c9ba-42b3-ba87-ae5ea5d3cac3
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e743464fcf482ea51f0cde78d692b367c2be525b
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="developing-a-user-interface-for-a-custom-foreach-enumerator"></a>Développement d'une interface utilisateur pour un énumérateur ForEach personnalisé
  Après avoir remplacé l'implémentation des propriétés et méthodes de la classe de base afin de fournir vos fonctionnalités personnalisées, vous pouvez créer une interface utilisateur personnalisée pour votre énumérateur Foreach. Si vous ne créez pas d'interface utilisateur personnalisée, les utilisateurs peuvent configurer uniquement le nouvel énumérateur Foreach personnalisé en utilisant la fenêtre Propriétés.  
  
 Dans un projet ou assembly d'interface utilisateur personnalisée, vous créez une classe qui implémente l'objet <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI>. Cette classe dérive de System.Windows.Forms.UserControl, qui est généralement utilisé pour créer un contrôle composite afin d’héberger d’autres contrôles Windows Forms. Le contrôle que vous créez s’affiche dans le **configuration de l’énumérateur** zone de la **Collection** onglet de la **éditeur de boucle Foreach**.  
  
> [!IMPORTANT]  
>  Après avoir signé et généré votre interface utilisateur personnalisée, puis l’installer dans le global assembly cache comme décrit dans [génération, déploiement et débogage des objets personnalisés](../../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md), n’oubliez pas de fournir le nom qualifié complet de cette classe dans le <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute.UITypeName%2A> propriété de la <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>.  
  
## <a name="coding-the-user-interface-control-class"></a>Codage de la classe de contrôle de l'interface utilisateur  
  
### <a name="initializing-the-user-interface"></a>Initialisation de l'interface utilisateur  
 Vous remplacez la méthode <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.Initialize%2A> pour mettre en cache des références à l'objet hôte et aux collections de gestionnaires de connexion et variables définies dans le package.  
  
### <a name="setting-properties-on-the-user-interface-control"></a>Définition de propriétés sur le contrôle de l'interface utilisateur  
 La classe UserControl, dont la classe d’interface utilisateur est dérivée, vise à utiliser comme un contrôle composite à héberger d’autres contrôles Windows Forms. Parce que cette classe héberge d'autres contrôles, vous pouvez concevoir votre interface utilisateur personnalisée en faisant glisser des contrôles, en les réorganisant, en définissant leurs propriétés et en répondant au moment de l'exécution à leurs événements comme dans toute application Windows Forms.  
  
### <a name="saving-settings"></a>Enregistrement des paramètres  
 Vous remplacez la méthode <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.SaveSettings%2A> pour copier les valeurs sélectionnées par l'utilisateur depuis les contrôles vers les propriétés de l'énumérateur lorsque l'utilisateur ferme l'éditeur.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un énumérateur Foreach personnalisé](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/creating-a-custom-foreach-enumerator.md)   
 [Codage d’un énumérateur Foreach personnalisé](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/coding-a-custom-foreach-enumerator.md)  
  
  


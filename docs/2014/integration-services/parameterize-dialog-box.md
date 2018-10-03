---
title: Paramétrer la boîte de dialogue | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.parameter.f1
ms.assetid: fac02b6d-d247-447a-8940-e8700c7ac350
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 76a48abe8ab2fe8481b2944ed6b3c77258b4c855
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48075601"
---
# <a name="parameterize-dialog-box"></a>Parameterize Dialog Box
  La boîte de dialogue **Paramétrer** vous permet d'associer un paramètre nouveau ou existant à la propriété d'une tâche. Vous ouvrez la boîte de dialogue en cliquant avec le bouton droit sur une tâche ou en affichant l'onglet Flux de contrôle dans le Concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] , puis en cliquant sur **Paramétrer**. La liste suivante décrit les éléments d'interface utilisateur de la boîte de dialogue. Pour plus d’informations sur les paramètres, consultez [Paramètres Integration Services &#40;SSIS&#41;](integration-services-ssis-package-and-project-parameters.md).  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 **Propriété**  
 Sélectionnez la propriété de la tâche que vous souhaitez associer à un paramètre. Cette liste est remplie avec toutes les propriétés qui sont paramétrables.  
  
 **Utiliser un paramètre existant**  
 Sélectionnez cette option pour associer la propriété de la tâche à un paramètre existant, puis sélectionnez le paramètre dans la liste déroulante.  
  
 **Ne pas utiliser de paramètre**  
 Sélectionnez cette option pour supprimer une référence à un paramètre. Le paramètre n'est pas supprimé.  
  
 **Créer un paramètre**  
 Sélectionnez cette option pour créer un nouveau paramètre que vous souhaitez associer à la propriété de la tâche.  
  
 **Nom**  
 Spécifiez le nom du paramètre à créer.  
  
 **Description**  
 Spécifiez la description du paramètre.  
  
 **Valeur**  
 Spécifiez la valeur par défaut du paramètre. Cette opération est aussi appelée « valeur par défaut de conception », qui peut être remplacée ultérieurement au moment du déploiement.  
  
 **Portée**  
 Spécifiez l'étendue du paramètre en sélectionnant l'option **Projet** ou **Package** . Les paramètres du projet sont utilisés pour fournir une entrée externe que le projet reçoit à un ou plusieurs packages du projet. L'utilisation de paramètres de package vous permet de modifier l'exécution du package sans avoir à modifier et à redéployer le package.  
  
 **Sensible**  
 Spécifiez si le paramètre contient une valeur sensible en activant ou en désactivant la case à cocher. Les valeurs de paramètre sensibles sont chiffrées dans le catalogue et apparaissent sous la forme d'une valeur Null lorsqu'elles sont affichées avec Transact-SQL ou SQL Server Management Studio.  
  
 **Obligatoire**  
 Spécifiez si le paramètre nécessite qu'une valeur, autre que la valeur de conception par défaut, soit spécifiée pour que le package puisse s'exécuter.  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
  

---
title: Paramétrer la boîte de dialogue | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.ssis.designer.parameter.f1
ms.assetid: fac02b6d-d247-447a-8940-e8700c7ac350
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 9a8f684eb94884d14c433539d2a617485379a784
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154652"
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
  
 **Value**  
 Spécifiez la valeur par défaut du paramètre. Cette opération est aussi appelée « valeur par défaut de conception », qui peut être remplacée ultérieurement au moment du déploiement.  
  
 **Portée**  
 Spécifiez l'étendue du paramètre en sélectionnant l'option **Projet** ou **Package** . Les paramètres du projet sont utilisés pour fournir une entrée externe que le projet reçoit à un ou plusieurs packages du projet. L'utilisation de paramètres de package vous permet de modifier l'exécution du package sans avoir à modifier et à redéployer le package.  
  
 **Sensible**  
 Spécifiez si le paramètre contient une valeur sensible en activant ou en désactivant la case à cocher. Les valeurs de paramètre sensibles sont chiffrées dans le catalogue et apparaissent sous la forme d'une valeur Null lorsqu'elles sont affichées avec Transact-SQL ou SQL Server Management Studio.  
  
 **Obligatoire**  
 Spécifiez si le paramètre nécessite qu'une valeur, autre que la valeur de conception par défaut, soit spécifiée pour que le package puisse s'exécuter.  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
  
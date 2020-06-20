---
title: Éditeur de tâche de transfert de messages d’erreur (page messages) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfererrormessagestask.errormessages.F1
helpviewer_keywords:
- Transfer Error Messages Task Editor
ms.assetid: cb2226a0-3037-4fdf-966f-81eabc0da9cf
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 2b21476bb6b696b51cc1932c171bdd8dfa1d0e6d
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84972834"
---
# <a name="transfer-error-messages-task-editor-messages-page"></a>Éditeur de tâche de transfert de messages d'erreur (page Messages)
  Utilisez la page **Messages** de la boîte de dialogue **Éditeur de tâche de transfert de messages d’erreur** pour spécifier les propriétés de copie d’un ou plusieurs messages d’erreur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] définis par l’utilisateur d’une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à une autre. Pour plus d'informations sur cette tâche, consultez [Transfer Error Messages Task](control-flow/transfer-error-messages-task.md).  
  
## <a name="options"></a>Options  
 **Abord SourceConnection**  
 Sélectionnez un gestionnaire de connexions SMO dans la liste ou cliquez sur **\<New connection...>** pour créer une nouvelle connexion au serveur source.  
  
 **DestinationConnection**  
 Sélectionnez un gestionnaire de connexions SMO dans la liste ou cliquez sur **\<New connection...>** pour créer une connexion au serveur de destination.  
  
 **IfObjectExists**  
 Déterminez si la tâche doit remplacer les messages d'erreur définis par l'utilisateur existants, ignorer les messages existants ou échouer si des messages d'erreur du même nom existent déjà sur le serveur de destination.  
  
 **TransferAllErrorMessages**  
 Déterminez si la tâche doit copier du serveur source au serveur de destination tous les messages définis par l'utilisateur ou seulement ceux spécifiés.  
  
 Cette propriété dispose des options répertoriées dans le tableau suivant :  
  
|Value|Description|  
|-----------|-----------------|  
|**:**|Copie tous les messages définis par l'utilisateur.|  
|**Fausses**|Copie uniquement les messages définis par l'utilisateur spécifiés.|  
  
 **ErrorMessagesList**  
 Cliquez sur le bouton Parcourir **(...)** pour sélectionner les messages d’erreur à copier.  
  
> [!NOTE]  
>  Vous devez spécifier **SourceConnection** avant de pouvoir sélectionner les messages d’erreur à copier.  
  
 **ErrorMessageLanguagesList**  
 Cliquez sur le bouton Parcourir **(...)** pour sélectionner les langues pour lesquelles copier les messages d’erreur définis par l’utilisateur sur le serveur de destination. Une version us_english (page de codes 1033) du message doit exister sur le serveur de destination avant de pouvoir transférer vers ce serveur d'autres versions de langue du message.  
  
> [!NOTE]  
>  Vous devez spécifier **SourceConnection** avant de pouvoir sélectionner les messages d’erreur à copier.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services de référence des erreurs et des messages](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Tâches Integration Services](control-flow/integration-services-tasks.md)   
 [Éditeur de tâche de transfert de messages d’erreur &#40;page général&#41;](general-page-of-integration-services-designers-options.md)   
 [Gestionnaire de connexions SMO](connection-manager/smo-connection-manager.md)   
 [Éditeur de tâche de transfert de messages d’erreur &#40;page général&#41;](general-page-of-integration-services-designers-options.md)   
 [Gestionnaire de connexions SMO](connection-manager/smo-connection-manager.md)  
  
  

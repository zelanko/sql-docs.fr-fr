---
title: Gérer un service Oracle CDC | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- createSrv
ms.assetid: 5972cee3-b1a9-4c56-aed6-bdddf84af283
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8fb328c6fb7418ad1aa239e63eb537e0857e345c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48073459"
---
# <a name="manage-an-oracle-cdc-service"></a>Manage an Oracle CDC Service
  Vous pouvez utiliser la console de configuration du service de capture de données modifiées pour gérer un service de capture de données modifiées spécifique.  
  
 **Pour sélectionner le service de capture de données modifiées à utiliser**  
  
1.  Dans le volet gauche de la console de configuration du service de capture de données modifiées, développez **Services de capture de données modifiées locaux**.  
  
2.  Sélectionnez le service de capture de données modifiées à utiliser.  
  
     Vous pouvez également cliquer avec le bouton droit sur le service de capture de données modifiées que vous souhaitez utiliser et sélectionner l'action souhaitée. Consultez [Opérations possibles avec un service de capture de données modifiées](manage-an-oracle-cdc-service.md#bkmk_whatcandowithcdcservice).  
  
 **OR**  
  
1.  Sélectionnez **Services de capture de données modifiées locaux** dans le volet gauche de la console de configuration du service de capture de données modifiées.  
  
2.  Dans la section centrale de la console de configuration du service de capture de données modifiées, sélectionnez le service que vous souhaitez utiliser.  
  
     Vous pouvez également cliquer avec le bouton droit sur le service de capture de données modifiées que vous souhaitez utiliser et sélectionner l'action souhaitée. Consultez [Opérations possibles avec un service de capture de données modifiées](manage-an-oracle-cdc-service.md#bkmk_whatcandowithcdcservice).  
  
##  <a name="BKMK_WhatcandowithCDCService"></a> What can you do with a CDC Service  
 Vous pouvez effectuer les actions suivantes lorsque vous utilisez un service de capture de données modifiées.  
  
### <a name="delete-the-service"></a>Supprimer le service  
 Dans le volet **Actions** à droite de la console de configuration du service de capture de données modifiées, cliquez sur **Supprimer** pour supprimer le service.  
  
 Vous pouvez également cliquer avec le bouton droit sur le service de capture de données modifiées à supprimer et sélectionner **Supprimer**.  
  
 **Remarque**: si le service est en cours d'exécution lors de sa suppression, il est arrêté avant d'être supprimé.  
  
 Pour supprimer la définition de service Windows de capture de données modifiées Oracle, le programme doit disposer d'un accès de mise à jour à la base de données MSXDBCDC dans l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] associée. Lorsque vous cliquez sur OK pour supprimer le service, le programme tente de supprimer l'inscription du service de capture de données modifiées Oracle dans la base de données MSXDBCDC. Si le programme ne peut pas supprimer l'inscription du service de capture de données modifiées Oracle, car il ne dispose pas des autorisations appropriées, il invite l'utilisateur à entrer une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec des autorisations de mise à jour de la base de données MSXDBCDC.  
  
 Pour plus d'informations sur les données que vous devez taper dans la boîte de dialogue Connexion à SQL Server, consultez [Connection to SQL Server for Delete](connection-to-sql-server-for-delete.md).  
  
### <a name="edit-the-cdc-service-properties"></a>Modifier les propriétés de service de capture de données modifiées  
 Dans le volet **Actions** à droite de la console de configuration du service de capture de données modifiées, cliquez sur **Propriétés**.  
  
 Vous pouvez également cliquer avec le bouton droit sur le service de capture de données modifiées où vous souhaitez modifier les propriétés et sélectionner **Propriétés**.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour gérer un service CDC local](how-to-manage-a-local-cdc-service.md)  
  
  

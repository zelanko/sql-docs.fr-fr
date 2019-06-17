---
title: Gestionnaire de connexions SMO | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], SMO
- SMO connection manager
- connection managers [Integration Services], SMO
ms.assetid: d273f1fb-a6a8-4f2f-a5ff-55c2e3de4723
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 32710f704e3d51d143e071178d690413735319f5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62833101"
---
# <a name="smo-connection-manager"></a>Gestionnaire de connexions SMO
  Un gestionnaire de connexions SMO permet à un package de se connecter à un serveur SMO (SQL Management Object). Les tâches de transfert incluses dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilisent un gestionnaire de connexions SMO. Par exemple, la tâche de transfert de connexions qui transfère des connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise un gestionnaire de connexions SMO.  
  
 Lorsque vous ajoutez un gestionnaire de connexions SMO à un package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée un gestionnaire de connexions qui sera résolu en tant que connexion SMO au moment de l'exécution, définit les propriétés du gestionnaire de connexions et ajoute le gestionnaire de connexions à la collection `Connections` sur le package. La propriété `ConnectionManagerType` du gestionnaire de connexions a pour valeur `SMOServer`.  
  
 Vous pouvez configurer le gestionnaire de connexions SMO de plusieurs manières :  
  
-   Spécifiez le nom d'un serveur sur lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est installé.  
  
-   Sélectionnez le mode d'authentification pour la connexion au serveur.  
  
## <a name="configuration-of-the-smo-connection-manager"></a>Configuration du gestionnaire de connexions SMO  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir dans le Concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , consultez [Éditeur du gestionnaire de connexions SMO](../smo-connection-manager-editor.md).  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programme](../building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Connexions Integration Services &#40;SSIS&#41;](integration-services-ssis-connections.md)  
  
  

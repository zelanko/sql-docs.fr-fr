---
title: Gestionnaire de connexions SMO | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connections [Integration Services], SMO
- SMO connection manager
- connection managers [Integration Services], SMO
ms.assetid: d273f1fb-a6a8-4f2f-a5ff-55c2e3de4723
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 2202cb3f505dc17dfd9f1bcd283c36ca78ef02d8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041161"
---
# <a name="smo-connection-manager"></a>Gestionnaire de connexions SMO
  Un gestionnaire de connexions SMO permet à un package de se connecter à un serveur SMO (SQL Management Object). Les tâches de transfert incluses dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilisent un gestionnaire de connexions SMO. Par exemple, la tâche de transfert de connexions qui transfère des connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise un gestionnaire de connexions SMO.  
  
 Lorsque vous ajoutez un gestionnaire de connexions SMO à un package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée une connexion de gestionnaire qui sera converti en une connexion SMO au moment de l’exécution, définit les propriétés du Gestionnaire des connexions et ajoute le Gestionnaire de connexions pour la `Connections` collection sur le package. Le `ConnectionManagerType` du Gestionnaire de connexions est définie sur `SMOServer`.  
  
 Vous pouvez configurer le gestionnaire de connexions SMO de plusieurs manières :  
  
-   Spécifiez le nom d'un serveur sur lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est installé.  
  
-   Sélectionnez le mode d'authentification pour la connexion au serveur.  
  
## <a name="configuration-of-the-smo-connection-manager"></a>Configuration du gestionnaire de connexions SMO  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir dans le Concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , consultez [Éditeur du gestionnaire de connexions SMO](../smo-connection-manager-editor.md).  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programme, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programme](../building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Services d’intégration &#40;SSIS&#41; connexions](integration-services-ssis-connections.md)  
  
  
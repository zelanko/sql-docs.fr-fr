---
title: Gestionnaire de connexions ODBC | Microsoft Docs
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
- connections [Integration Services], ODBC
- ODBC connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], ODBC
ms.assetid: e8c77aa7-6772-485e-918e-cef9eeb18c58
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 9453dc6e402fce60e1f4f440d84f882e513abea7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051995"
---
# <a name="odbc-connection-manager"></a>Gestionnaire de connexions ODBC
  Un gestionnaire de connexions ODBC permet à un package de se connecter à divers systèmes de gestion de base de données à l'aide de la spécification ODBC (Open Database Connectivity).  
  
 Lorsque vous ajoutez une connexion ODBC à un package et que vous définissez les propriétés du gestionnaire, connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée une connexion de gestionnaire et ajoute le Gestionnaire de connexions pour la `Connections` collection du package. Au moment de l'exécution, le gestionnaire de connexions est résolu en tant que connexion ODBC physique.  
  
 Le `ConnectionManagerType` du Gestionnaire de connexions est définie sur `ODBC`.  
  
 Vous pouvez configurer le gestionnaire de connexions ODBC de plusieurs manières :  
  
-   Fournissez une chaîne de connexion qui fait référence à un nom d'utilisateur ou de source de données système.  
  
-   Spécifiez le serveur auquel se connecter.  
  
-   Indiquez si la connexion est conservée au moment de l'exécution.  
  
## <a name="configuration-of-the-odbc-connection-manager"></a>Configuration du gestionnaire de connexions ODBC  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur l’une des rubriques suivantes :  
  
-   [Référence de l’interface utilisateur du Gestionnaire de connexions ODBC](../odbc-connection-manager-ui-reference.md)  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programme, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programme](../building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Services d’intégration &#40;SSIS&#41; connexions](integration-services-ssis-connections.md)  
  
  
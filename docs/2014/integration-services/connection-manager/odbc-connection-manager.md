---
title: Gestionnaire de connexions ODBC | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], ODBC
- ODBC connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], ODBC
ms.assetid: e8c77aa7-6772-485e-918e-cef9eeb18c58
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 701ea85cafc22d9ea850e18310c3c2d06748cb08
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85438356"
---
# <a name="odbc-connection-manager"></a>Gestionnaire de connexions ODBC
  Un gestionnaire de connexions ODBC permet à un package de se connecter à divers systèmes de gestion de base de données à l'aide de la spécification ODBC (Open Database Connectivity).  
  
 Lorsque vous ajoutez une connexion ODBC à un package et définissez les propriétés du gestionnaire de connexions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée un gestionnaire de connexions et ajoute le gestionnaire de connexions à la `Connections` collection du package. Au moment de l'exécution, le gestionnaire de connexions est résolu en tant que connexion ODBC physique.  
  
 La propriété `ConnectionManagerType` du gestionnaire de connexions a pour valeur `ODBC`.  
  
 Vous pouvez configurer le gestionnaire de connexions ODBC de plusieurs manières :  
  
-   Fournissez une chaîne de connexion qui fait référence à un nom d'utilisateur ou de source de données système.  
  
-   Spécifiez le serveur auquel se connecter.  
  
-   Indiquez si la connexion est conservée au moment de l'exécution.  
  
## <a name="configuration-of-the-odbc-connection-manager"></a>Configuration du gestionnaire de connexions ODBC  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir dans le Concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur une des rubriques suivantes :  
  
-   [Informations de référence sur l’interface utilisateur du gestionnaire de connexions ODBC](../odbc-connection-manager-ui-reference.md)  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programme](../building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Connexions Integration Services &#40;SSIS&#41;](integration-services-ssis-connections.md)  
  
  

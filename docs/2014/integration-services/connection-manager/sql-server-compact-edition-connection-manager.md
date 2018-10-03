---
title: Gestionnaire de connexions de SQL Server Compact Edition | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Compact, connection manager
- connections [Integration Services], SQL Server Compact
- connection managers [Integration Services], SQL Server Compact
ms.assetid: ba627d4d-41f4-49fc-a921-f534cde67770
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4fd067d6f01c168861a42895c36024cb4c0a9aa5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48082789"
---
# <a name="sql-server-compact-edition-connection-manager"></a>Gestionnaire de connexions de SQL Server Compact Edition
  Un gestionnaire de connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact permet à un package de se connecter à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact. La destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact incluse dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilise ce gestionnaire de connexions pour charger des données dans une table d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
> [!NOTE]  
>  Sur un ordinateur 64 bits, vous devez exécuter les packages qui se connectent à des sources de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact en mode 32 bits. Le fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact utilisé par [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour se connecter à des sources de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact n’est disponible qu’en version 32 bits.  
  
## <a name="configuration-the-sql-server-compact-edition-connection-manager"></a>Configuration du gestionnaire de connexions SQL Server Compact Edition  
 Lorsque vous ajoutez un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Gestionnaire de connexions Compact à un package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée une connexion de gestionnaire qui sera converti en un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion Compact au moment de l’exécution, définit les propriétés du Gestionnaire des connexions et ajoute le Gestionnaire de connexion à la `Connections` collection sur le package.  
  
 Le `ConnectionManagerType` propriété du Gestionnaire de connexions est définie sur `SQLMOBILE`.  
  
 Vous pouvez configurer le gestionnaire de connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact de plusieurs manières :  
  
-   Spécifiez une chaîne de connexion qui indique l’emplacement de la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
-   Spécifiez un mot de passe pour une base de données protégée par mot de passe.  
  
-   Spécifiez le serveur où est stockée la base de données.  
  
-   Indiquez si la connexion créée à partir du gestionnaire de connexions est conservée au moment de l'exécution.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur l'une des rubriques suivantes :  
  
-   [SQL Server Compact Edition Connection Manager Editor &#40;Page de connexion&#41;](../sql-server-compact-edition-connection-manager-editor-connection-page.md)  
  
-   [SQL Server Compact Edition Connection Manager Editor &#40;Page toutes les&#41;](../sql-server-compact-edition-connection-manager-editor-all-page.md)  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programmation](../building-packages-programmatically/adding-connections-programmatically.md).  
  
  

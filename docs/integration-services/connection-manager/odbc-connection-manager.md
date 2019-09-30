---
title: Gestionnaire de connexions ODBC | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.odbcconnection.f1
helpviewer_keywords:
- connections [Integration Services], ODBC
- ODBC connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], ODBC
ms.assetid: e8c77aa7-6772-485e-918e-cef9eeb18c58
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b0d115753447a337cc9846942e2c39da54f3658f
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71298496"
---
# <a name="odbc-connection-manager"></a>Gestionnaire de connexions ODBC

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Un gestionnaire de connexions ODBC permet à un package de se connecter à divers systèmes de gestion de base de données à l'aide de la spécification ODBC (Open Database Connectivity).  
  
 Quand vous ajoutez une connexion ODBC à un package et que vous définissez les propriétés du gestionnaire de connexions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée un gestionnaire de connexions et l’ajoute à la collection **Connections** du package. Au moment de l'exécution, le gestionnaire de connexions est résolu en tant que connexion ODBC physique.  
  
 La propriété **ConnectionManagerType** du gestionnaire de connexions a pour valeur **ODBC**.  
  
 Vous pouvez configurer le gestionnaire de connexions ODBC de plusieurs manières :  
  
-   Fournissez une chaîne de connexion qui fait référence à un nom d'utilisateur ou de source de données système.  
  
-   Spécifiez le serveur auquel se connecter.  
  
-   Indiquez si la connexion est conservée au moment de l'exécution.  
  
## <a name="configuration-of-the-odbc-connection-manager"></a>Configuration du gestionnaire de connexions ODBC  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur l’une des rubriques suivantes :  
  
-   [Informations de référence sur l’interface utilisateur du gestionnaire de connexions ODBC](../../integration-services/connection-manager/odbc-connection-manager-ui-reference.md)  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programme](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="odbc-connection-manager-ui-reference"></a>Référence de l'interface utilisateur du gestionnaire de connexions ODBC
  Utilisez la boîte de dialogue **Configurer le gestionnaire de connexions ODBC** pour ajouter une connexion à une source de données ODBC.  
  
 Pour en savoir plus sur le gestionnaire de connexions ODBC, consultez [ODBC Connection Manager](../../integration-services/connection-manager/odbc-connection-manager.md).  
  
### <a name="options"></a>Options  
 **Connexions de données**  
 Sélectionnez un gestionnaire de connexions ODBC existant dans la liste.  
  
 **Propriétés des connexions de données**  
 Affichez les propriétés et les valeurs du gestionnaire de connexions ODBC sélectionné.  
  
 **Nouveau**  
 Créez un gestionnaire de connexions ODBC à l’aide de la boîte de dialogue **Gestionnaire de connexions** . Cette boîte de dialogue vous permet également de créer une nouvelle source de données ODBC si nécessaire.  
  
 **Supprimer**  
 Sélectionnez une connexion, puis supprimez-la à l’aide du bouton **Supprimer** .  
## <a name="see-also"></a>Voir aussi  
 [Connexions Integration Services &#40;SSIS&#41;](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  

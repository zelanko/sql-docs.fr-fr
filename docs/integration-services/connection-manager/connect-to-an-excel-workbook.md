---
title: "Se connecter à un classeur Excel | Documents Microsoft"
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: connection-manager
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Excel [Integration Services]
ms.assetid: d9746318-3669-4ce2-bbb0-4a1bd471c9dd
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2800075091835b2d6f2b07ee34e9b897fe86634e
ms.openlocfilehash: f8fb1db80ac1b750950a3401516b54af5ee29686
ms.contentlocale: fr-fr
ms.lasthandoff: 08/17/2017

---
# <a name="connect-to-an-excel-workbook"></a>Établir une connexion à un classeur Excel
  Pour connecter un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] à un classeur Microsoft Office Excel, vous devez utiliser un gestionnaire de connexions Excel.  
  
 Vous pouvez créer ces gestionnaires de connexions à partir de la zone Gestionnaires de connexions dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou à partir de l’Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
 
## <a name="connectivity-components-for-microsoft-excel-and-access-files"></a>Composants de connectivité pour les fichiers Microsoft Excel et Access
  
Vous devrez peut-être télécharger les composants de connectivité pour les fichiers Microsoft Office, s’ils ne sont pas déjà installés. Téléchargez la dernière version des composants de connectivité pour les fichiers Excel et Access ici : [redistribuable de 2016 du moteur de base de données de Microsoft Access](https://www.microsoft.com/download/details.aspx?id=54920).
  
La dernière version des composants permettre ouvrir des fichiers créés par les versions antérieures d’Excel.

Si l’ordinateur dispose d’une version 32 bits d’Office, vous devez installer la version 32 bits des composants et vous devez également vous assurer que vous exécutez le package en mode 32 bits.

Si vous avez un abonnement Office 365, assurez-vous que vous téléchargez le redistribuable de 2016 moteur de base de données Access et non le Runtime de 2016 pour Microsoft Access. Lorsque vous exécutez le programme d’installation, vous voyez un message d’erreur que vous ne pouvez pas installer le téléchargement côte à côte avec les composants Office-clic. Pour ignorer ce message d’erreur et d’installer les composants correctement, exécutez l’installation en mode silencieux en ouvrant une fenêtre d’invite de commandes et en exécutant le. Fichier .exe que vous avez téléchargé avec le `/quiet` basculer. Par exemple :

`C:\Users\<user name>\Downloads\AccessDatabaseEngine.exe /quiet`

## <a name="create-an-excel-connection-manager"></a>Création d’Excel Gestionnaire de connexions

### <a name="to-create-an-excel-connection-manager-from-the-connection-managers-area"></a>Pour créer un gestionnaire de connexions Excel à partir de la zone Gestionnaires de connexions  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le package.  
  
2.  Cliquez avec le bouton droit dans la zone **Gestionnaires de connexions** et sélectionnez **Nouvelle connexion**.  
  
3.  Dans la boîte de dialogue **Ajout d’un gestionnaire de connexions SSIS** , sélectionnez **Excel**, puis configurez le gestionnaire de connexions.  
  
     Pour plus d’informations sur les options de configuration qui sont disponibles pour ce gestionnaire de connexions, consultez [Éditeur du gestionnaire de connexions Excel](../../integration-services/connection-manager/excel-connection-manager-editor.md).  
  
### <a name="to-create-an-excel-connection-from-the-sql-server-import-and-export-wizard"></a>Pour créer une connexion à Excel à partir de l'Assistant Importation et Exportation SQL Server  
  
1.  Démarrez la version 32 bits de l’Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
2.  Dans la page **Choisir une source de données** , pour **Source de données**, sélectionnez **Microsoft Excel**, puis configurez la connexion à Excel.  
  
     Pour plus d’informations sur les options de configuration qui sont disponibles pour ce type de connexion, consultez [Éditeur du gestionnaire de connexions Excel](../../integration-services/connection-manager/excel-connection-manager-editor.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Établir une connexion à une base de données Access](../../integration-services/connection-manager/connect-to-an-access-database.md)  
  
  


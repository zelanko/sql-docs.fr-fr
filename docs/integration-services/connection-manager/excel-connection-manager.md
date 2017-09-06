---
title: Gestionnaire de connexions Excel | Documents Microsoft
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.excelconnection.f1
helpviewer_keywords:
- files [Integration Services], connections
- connections [Integration Services], Excel
- Excel [Integration Services]
- connection managers [Integration Services], Excel
ms.assetid: 667419f2-74fb-4b50-b963-9197d1368cda
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2800075091835b2d6f2b07ee34e9b897fe86634e
ms.openlocfilehash: a5ce75f3c1715870113626642150028e31a0d58b
ms.contentlocale: fr-fr
ms.lasthandoff: 08/17/2017

---
# <a name="excel-connection-manager"></a>Gestionnaire de connexions Excel
  Un gestionnaire de connexions Excel permet à un package de se connecter à un fichier [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel. La source et la destination Excel incluses dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilisent le gestionnaire de connexions Excel.  
  
 Quand vous ajoutez un gestionnaire de connexions Excel à un package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée un gestionnaire de connexions qui est converti en connexion Excel au moment de l’exécution, définit les propriétés du gestionnaire de connexions et ajoute le gestionnaire de connexions à la collection **Connections** du package.  
  
 La propriété **ConnectionManagerType** du gestionnaire de connexions a pour valeur **EXCEL**.  
  
## <a name="configuration-of-the-excel-connection-manager"></a>Configuration du gestionnaire de connexions Excel  
 Vous pouvez configurer le gestionnaire de connexions Excel de plusieurs manières :  
  
-   Spécifiez le chemin d'accès du fichier Excel.  
  
    > [!NOTE]  
    >  Vous ne pouvez pas vous connecter à un fichier Excel protégé par mot de passe.  
  
-   Spécifiez la version d'Excel utilisée pour créer le fichier.  
  
-   Indiquez si la première ligne des données qui ont fait l'objet d'un accès dans les feuilles de calcul ou les plages sélectionnées contient les noms de colonnes.  
  
 Si le gestionnaire de connexions Excel est utilisé par une source Excel, les noms de colonnes sont inclus avec les données extraites. S'il est utilisé par une destination Excel, les noms de colonnes sont inclus dans les données écrites.  
  
 Pour plus d’informations sur le comportement des sources et des destinations Excel, consultez [Excel Source](../../integration-services/data-flow/excel-source.md) et [Excel Destination](../../integration-services/data-flow/excel-destination.md).  
  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , consultez [Éditeur du gestionnaire de connexions Excel](../../integration-services/connection-manager/excel-connection-manager-editor.md).  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programmation](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
 Pour plus d’informations sur le bouclage dans un groupe de fichiers Excel, consultez [Effectuer une boucle dans des fichiers et des tables Excel en utilisant un conteneur de boucles Foreach](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md).  
  
## <a name="excel-connection-manager-editor"></a>Éditeur du gestionnaire de connexions Excel
  La boîte de dialogue **Éditeur du gestionnaire de connexions Excel** vous permet d'ajouter une connexion à un classeur [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] existant ou nouveau.  
  
 Pour en savoir plus sur le gestionnaire de connexions Excel, consultez [Excel Connection Manager](../../integration-services/connection-manager/excel-connection-manager.md).  
  
### <a name="options"></a>Options  
 **Chemin de fichier Excel**  
 Tapez le chemin d'accès et le nom du fichier d'un classeur Excel (.xls) existant ou nouveau.  
  
> [!NOTE]  
>  Vous ne pouvez pas vous connecter à un fichier Excel protégé par mot de passe.  
  
> [!WARNING]  
>  **L’Éditeur de destination Excel** crée automatiquement le fichier Excel quand vous sélectionnez une **Connexion Excel** qui pointe vers un fichier nouveau ou inexistant, et que vous cliquez sur **Nouveau** dans **Nom de la feuille Excel**.  
  
 **Parcourir**  
 Utilisez la boîte de dialogue **Ouvrir** pour rechercher le dossier dans lequel le fichier Excel se trouve ou accéder à l’emplacement où vous souhaitez créer le fichier.  
  
 **Version Excel**  
 Spécifiez la version de Microsoft Excel qui a été utilisée pour créer le fichier.  
  
 **La première ligne possède des noms de colonnes**  
 Permet de spécifier si la première ligne de données dans la feuille de calcul sélectionnée contient les noms des colonnes. La valeur par défaut de cette option est **True**.  
  
## <a name="connectivity-components-for-microsoft-excel-and-access-files"></a>Composants de connectivité pour les fichiers Microsoft Excel et Access
  
Vous devrez peut-être télécharger les composants de connectivité pour les fichiers Microsoft Office, s’ils ne sont pas déjà installés. Téléchargez la dernière version des composants de connectivité pour les fichiers Excel et Access ici : [redistribuable de 2016 du moteur de base de données de Microsoft Access](https://www.microsoft.com/download/details.aspx?id=54920).
  
La dernière version des composants permettre ouvrir des fichiers créés par les versions antérieures d’Excel.

Si l’ordinateur dispose d’une version 32 bits d’Office, vous devez installer la version 32 bits des composants et vous devez également vous assurer que vous exécutez le package en mode 32 bits.

Si vous avez un abonnement Office 365, assurez-vous que vous téléchargez le redistribuable de 2016 moteur de base de données Access et non le Runtime de 2016 pour Microsoft Access. Lorsque vous exécutez le programme d’installation, vous voyez un message d’erreur que vous ne pouvez pas installer le téléchargement côte à côte avec les composants Office-clic. Pour ignorer ce message d’erreur, exécutez l’installation en mode silencieux en ouvrant une fenêtre d’invite de commandes et en exécutant le. Fichier .exe que vous avez téléchargé avec le `/quiet` basculer. Par exemple :

`C:\Users\<user name>\Downloads\AccessDatabaseEngine.exe /quiet`
  
## <a name="related-tasks"></a>Tâches associées  
  
-   [Effectuer une boucle dans des fichiers et des tables Excel en utilisant un conteneur de boucles Foreach](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
-   [Établir une connexion à un classeur Excel](../../integration-services/connection-manager/connect-to-an-excel-workbook.md)  
  
  

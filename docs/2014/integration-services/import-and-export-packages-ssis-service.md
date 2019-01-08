---
title: Importer et exporter des Packages (Service SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], importing
- packages [Integration Services], exporting
- importing packages
- exporting packages
ms.assetid: ef18ec11-b536-47d9-abd1-794099f43486
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2ba210106a7a4045c3dae43db3590e69a7c2c5ea
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52515789"
---
# <a name="import-and-export-packages-ssis-service"></a>Importer et exporter des packages (Service SSIS)
    
> [!IMPORTANT]  
>  Cette rubrique présente le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , un service Windows qui permet de gérer les packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] prend en charge le service pour la compatibilité avec les versions antérieures de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. À compter de [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], vous pouvez gérer des objets tels que des packages sur le serveur Integration Services.  
  
 Les packages peuvent être enregistrés dans la table sysssispackages de la base de données msdb de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ou dans le système de fichiers.  
  
 Le magasin de packages, qui est le stockage logique que le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contrôle et gère, peut inclure la base de données msdb et les dossiers du système de fichiers spécifiés dans le fichier de configuration pour le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
 Vous pouvez importer et exporter des packages entre les types de stockage suivants :  
  
-   Les dossiers du système de fichiers n'importe où dans le système de fichiers.  
  
-   Les dossiers dans le magasin de packages SSIS. Les deux dossiers par défaut sont appelés « Système de fichiers » et « MSDB ».  
  
-   La base de données msdb [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] vous donne la possibilité d'importer et d'exporter des packages, et ce faisant, de modifier le format et l'emplacement de stockage des packages. Les fonctionnalités d’importation et d’exportation vous permettent d’ajouter des packages au système de fichiers, au magasin de packages ou à la base de données msdb, et de copier des packages d’un format de stockage vers un autre. Par exemple, les packages enregistrés dans msdb peuvent être copiés dans le système de fichiers et vice versa.  
  
 Vous pouvez aussi copier un package dans un format différent à l’aide de l’utilitaire d’invite de commandes **dtutil** (dtutil.exe). Pour plus d’informations, consultez [dtutil Utility](dtutil-utility.md).  
  
## <a name="to-import-or-export-a-package"></a>Pour exporter ou importer un package  
  
> [!IMPORTANT]  
>  Cette rubrique décrit le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , qui fait partie de [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]. [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] prend en charge le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] pour la compatibilité descendante avec [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]. Pour plus d’informations sur la gestion des packages dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], consultez [Serveur Integration Services &#40;SSIS&#41;](catalog/integration-services-ssis-server-and-catalog.md).  
  
 Vous pouvez importer ou exporter un package [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] depuis ou vers les emplacements suivants :  
  
-   Vous pouvez importer un package stocké dans une instance de [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], dans le système de fichiers ou dans le magasin de packages [!INCLUDE[ssIS](../includes/ssis-md.md)] . Le package importé est enregistré dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ou dans un dossier dans le magasin de packages [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
-   Vous pouvez exporter un package stocké dans une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], dans le système de fichiers ou dans le magasin de packages [!INCLUDE[ssIS](../includes/ssis-md.md)] vers un format ou un emplacement de stockage différent.  
  
 Toutefois, il existe des restrictions relatives à l'importation et à l'exportation d'un package entre des versions différentes de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:  
  
-   Vous pouvez importer dans une instance de [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]des packages provenant d'une instance de [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], mais vous ne pouvez pas exporter de packages vers une instance de [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)].  
  
-   Dans une instance de [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], vous ne pouvez pas importer de packages provenant d'une instance de [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], ni exporter de packages vers une telle instance.  
  
 Les procédures ci-dessous montrent comment utiliser [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour importer et exporter un package.  
  
#### <a name="to-import-a-package-by-using-sql-server-management-studio"></a>Pour importer un package à l'aide de SQL Server Management Studio  
  
1.  Cliquez sur **Démarrer**, pointez sur **Microsoft** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], puis cliquez sur **SQL Server Management Studio**.  
  
2.  Dans la boîte de dialogue **Se connecter au serveur** , définissez les options suivantes :  
  
    -   Dans la zone **Type de serveur** , sélectionnez **Integration Services**.  
  
    -   Dans la zone **Nom du serveur**, indiquez le nom du serveur ou cliquez sur **\<Parcourir...>**, puis recherchez le serveur à utiliser.  
  
3.  Si l'Explorateur d'objets n'est pas ouvert, dans le menu **Affichage** , cliquez sur **Explorateur d'objets**.  
  
4.  Dans l'Explorateur d'objets, développez le dossier **Packages stockés** .  
  
5.  Développez les sous-dossiers afin de rechercher celui dans lequel vous souhaitez importer un package.  
  
6.  Cliquez avec le bouton droit sur le dossier, puis cliquez sur **Importer un package**. Effectuez ensuite l'une des opérations suivantes :  
  
    -   Pour importer à partir d'une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], sélectionnez l'option **SQL Server** , puis spécifiez le serveur et le mode d'authentification. Si vous sélectionnez l'authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , indiquez un nom d'utilisateur et un mot de passe.  
  
         Cliquez sur le bouton Parcourir **(...)**, sélectionnez le package à importer, puis cliquez sur **OK**.  
  
    -   Pour importer à partir d'un système de fichiers, sélectionnez l'option **Système de fichiers** .  
  
         Cliquez sur le bouton Parcourir **(...)**, sélectionnez le package à importer, puis cliquez sur **Ouvrir**.  
  
    -   Pour importer à partir du magasin de packages [!INCLUDE[ssIS](../includes/ssis-md.md)] , sélectionnez l'option **Magasin de packages SSIS** et spécifiez le serveur.  
  
         Cliquez sur le bouton Parcourir **(...)**, sélectionnez le package à importer, puis cliquez sur **OK**.  
  
7.  Si vous le souhaitez, mettez à jour le nom du package.  
  
8.  Pour mettre à jour le niveau de protection du package, cliquez sur le bouton Parcourir **(...)** et sélectionnez un niveau de protection différent dans la boîte de dialogue **Niveau de protection du package** . Si l'option **Chiffrer les données sensibles avec un mot de passe** ou **Chiffrer toutes les données avec un mot de passe** est sélectionnée, tapez un mot de passe et confirmez-le.  
  
9. Cliquez sur **OK** pour terminer l'importation.  
  
#### <a name="to-export-a-package-by-using-sql-server-management-studio"></a>Pour exporter un package à l'aide de SQL Server Management Studio  
  
1.  Cliquez sur **Démarrer**, pointez sur **Microsoft** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], puis cliquez sur **SQL Server Management Studio**.  
  
2.  Dans la boîte de dialogue **Se connecter au serveur** , définissez les options suivantes :  
  
    -   Dans la zone **Type de serveur** , sélectionnez **Integration Services**.  
  
    -   Dans la zone **Nom du serveur**, indiquez le nom du serveur ou cliquez sur **\<Parcourir...>**, puis recherchez le serveur à utiliser.  
  
3.  Si l'Explorateur d'objets n'est pas ouvert, dans le menu **Affichage** , cliquez sur **Explorateur d'objets**.  
  
4.  Dans l'Explorateur d'objets, développez le dossier **Packages stockés** .  
  
5.  Développez les sous-dossiers pour localiser le package à exporter.  
  
6.  Cliquez avec le bouton droit sur le package, cliquez sur **Exporter**, puis effectuez l’une des opérations suivantes :  
  
    -   Pour exporter un package vers une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], sélectionnez l'option **SQL Server** , puis indiquez le serveur et sélectionnez le mode d'authentification. Si vous sélectionnez l'authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , indiquez un nom d'utilisateur et un mot de passe.  
  
         Cliquez sur le bouton Parcourir **(...)**, puis développez le dossier **Packages SSIS** pour rechercher le dossier dans lequel enregistrer le package. Si vous le souhaitez, mettez à jour le nom par défaut du package, puis cliquez sur **OK**.  
  
    -   Pour exporter un package vers le système de fichiers, sélectionnez l'option **Système de fichiers** .  
  
         Cliquez sur le bouton Parcourir **(...)** pour rechercher le dossier dans lequel exporter le package, tapez le nom du fichier de package, puis cliquez sur **Enregistrer**.  
  
    -   Pour exporter un package vers le magasin de packages [!INCLUDE[ssIS](../includes/ssis-md.md)] , sélectionnez l'option **Magasin de packages SSIS** , puis indiquez le serveur.  
  
         Cliquez sur le bouton Parcourir **(...)**, développez le dossier **Packages SSIS**, puis sélectionnez le dossier dans lequel enregistrer le package. Si vous le souhaitez, entrez un nouveau nom pour le package dans la zone de texte **Nom du package** . [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  Pour mettre à jour le niveau de protection du package, cliquez sur le bouton Parcourir **(...)** et sélectionnez un niveau de protection différent dans la boîte de dialogue **Niveau de protection du package** . Si l'option **Chiffrer les données sensibles avec un mot de passe** ou **Chiffrer toutes les données avec un mot de passe** est sélectionnée, tapez un mot de passe et confirmez-le.  
  
8.  Cliquez sur **OK** pour terminer l'exportation.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de packages &#40;Service SSIS&#41;](service/package-management-ssis-service.md)  
  
  

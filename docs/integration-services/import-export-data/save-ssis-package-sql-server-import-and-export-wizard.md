---
title: "Enregistrer le package SSIS (Assistant Importation et Exportation SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "02/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.impexpwizard.savedtspackage.f1"
ms.assetid: 7bf8ac6a-5599-43ab-bf5c-e072c11b85a0
caps.latest.revision: 64
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 61
---
# Enregistrer le package SSIS (Assistant Importation et Exportation SQL Server)
  Si vous avez indiqué dans la page **Enregistrer et exécuter le package** que vous souhaitez enregistrer le package SSIS créé par l’Assistant, l’Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affiche l’option **Enregistrer le package SSIS**. Cette page vous permet de spécifier d’autres options pour l’enregistrement du package.  

Les options proposées dans la page **Enregistrer le package SSIS** varient en fonction du choix que vous avez effectué préalablement dans la page **Enregistrer et exécuter le package** pour l’enregistrement du package : dans SQL Server ou dans le système de fichiers. Pour avoir un autre aperçu de la page **Enregistrer et exécuter le package**, consultez [Enregistrer et exécuter le package](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md).
 
**Qu’est-ce qu’un package ?** L’Assistant utilise SQL Server Integration Services (SSIS) pour copier les données. Dans SSIS, l’unité de base est le package. L’Assistant crée un package SSIS en mémoire à mesure que vous parcourez les pages de l’Assistant et spécifiez les options.
 
## <a name="screen-shot---save-the-package-in-the-file-system"></a>Capture d’écran : Enregistrer le package dans le système de fichiers
 
La capture d’écran suivante illustre la page **Enregistrer le package SSIS** de l’Assistant une fois l’option **Système de fichiers** sélectionnée dans la page **Enregistrer et exécuter le package**. 
  
![Save SSIS Package page of the Import and Export Wizard](../../integration-services/import-export-data/media/save-package1.png "Save SSIS Package page of the Import and Export Wizard")  

## <a name="screen-shot---save-the-package-in-sql-server"></a>Capture d’écran : Enregistrer le package dans SQL Server

 La capture d’écran suivante illustre la page **Enregistrer le package SSIS** de l’Assistant une fois l’option **SQL Server** sélectionnée dans la page **Enregistrer et exécuter le package**. 
  
![Save SSIS Package page of the Import and Export Wizard](../../integration-services/import-export-data/media/save-package2.png "Save SSIS Package page of the Import and Export Wizard")  
  
## <a name="provide-a-name-and-description-for-the-package"></a>Fournir un nom et une description pour le package  
 **Nom**  
 Permet de spécifier un nom unique pour le package.  
  
 **Description**  
 Permet de décrire le package. En guise de bonne pratique, il est recommandé de décrire la fonction du package de façon à le documenter et à en faciliter la gestion.  
  
 **Cible**  
 Destination ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou système de fichiers) que vous avez définie préalablement pour le package. Si vous voulez enregistrer le package vers une autre destination, revenez à la page **Enregistrer et exécuter le package**.
  
## <a name="save-the-package-in-the-file-system"></a>Enregistrer le package dans le système de fichiers 
Si vous avez sélectionné le système de fichiers comme destination, vous devez compléter les champs suivants.

 **Nom de fichier**  
 Tapez le chemin et le nom du fichier de destination ou servez-vous du bouton **Parcourir** pour sélectionner une destination.  
  
> [!TIP] Veillez à spécifier un dossier de destination, soit en le tapant, soit en le recherchant dans l’arborescence. Si vous tapez le nom du fichier sans le chemin, vous ne saurez pas à quel emplacement l’Assistant enregistrera le package. Par ailleurs, il se peut que l’Assistant tente d’enregistrer le package à un emplacement auquel vous n’êtes pas autorisé à enregistrer un fichier, ce qui générera une erreur.  
>   
>  Souvenez-vous de l’endroit où vous enregistrez le fichier du package.  
  
 **Parcourir**  
 Vous pouvez éventuellement rechercher et sélectionner le chemin du fichier de destination via la boîte de dialogue **Enregistrer le package**.  

## <a name="save-the-package-in-sql-server"></a>Enregistrer le package dans SQL Server 
Si vous avez sélectionné une destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez compléter les champs suivants.

L’Assistant enregistre le package dans la base de données **msdb** de la table **sysssispackages**.
 
 > [!NOTE] Cette option n’enregistre pas le package dans la base de données du catalogue SSIS (SSISDB).  
 
 **Nom du serveur**  
 Tapez ou sélectionnez le nom du serveur de destination.  
   
 **Utiliser l’authentification Windows**  
Connectez-vous au serveur à l’aide de l’authentification intégrée Windows. Il s'agit de la méthode d'authentification conseillée.  
  
 **Utiliser l’authentification SQL Server**  
Connectez-vous au serveur à l’aide de l’authentification SQL Server.  
  
 **Nom d’utilisateur**  
Si vous avez spécifié l’authentification SQL Server, tapez le nom d’utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Mot de passe**  
Si vous avez spécifié l’authentification SQL Server, tapez le mot de passe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="about-the-two-pages-of-options-for-saving-the-package"></a>Présentation des deux pages d’options pour l’enregistrement du package  
 La page **Enregistrer le package SSIS** est l’une des deux pages dans lesquelles vous choisissez les options d’enregistrement du package SSIS.  
  
-   Dans la page précédente, **Enregistrer et exécuter le package**, vous choisissez d’enregistrer le package dans SQL Server ou sous forme de fichier. Vous pouvez aussi y sélectionner les paramètres de sécurité pour le package enregistré. Pour avoir un autre aperçu de la page **Enregistrer et exécuter le package**, consultez [Enregistrer et exécuter le package](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md).  
  
-   Dans la page active, vous indiquez un nom pour le package et des informations complémentaires sur l’emplacement où doit être enregistré le package.  
 
## <a name="run-the-saved-package-again-later"></a>Réexécuter le package enregistré à un moment ultérieur  
 Pour savoir comment réexécuter le package enregistré à un moment ultérieur, consultez l’une les rubriques suivantes.  
  
-   Pour exécuter un package en utilisant un utilitaire doté d’une interface utilisateur conviviale, consultez [Référence de l’interface utilisateur de l’utilitaire d’exécution de package &#40;DtExecUI&#41;](../../integration-services/packages/execute-package-utility-dtexecui-ui-reference.md).  
  
-   Pour exécuter un package à partir de la ligne de commande ou d’un fichier de commandes, consultez [Utilitaire dtexec](../../integration-services/packages/dtexec-utility.md).  
  
-   Si vous avez enregistré le package dans le système de fichiers, consultez [Exécuter un package dans les outils de données SQL Server](../../integration-services/packages/run-a-package-in-sql-server-data-tools.md) pour exécuter le package dans l’environnement de développement. Vous devez ajouter le package à un projet Integration Services pour pouvoir l’ouvrir et l’exécuter.  
 
-   Si vous avez enregistré le package dans SQL Server dans la base de données **msdb**, connectez-vous au service Integration Services. Ensuite, dans SQL Server Management Studio, dans l’Explorateur d’objets, accédez à **Packages stockés | MSDB**, cliquez avec le bouton droit sur le package, puis sélectionnez **Exécuter le package**.

## <a name="customize-the-saved-package"></a>Personnaliser le package enregistré  
 Pour savoir comment personnaliser le package enregistré, consultez [Packages Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-packages.md).  
  
## <a name="whats-next"></a>Étape suivante  
 Une fois que vous avez spécifié les autres options d’enregistrement du package, la page suivante s’intitule **Terminer l’Assistant**. Cette page vous permet d’examiner les choix effectués dans l’Assistant et de lancer l’opération. Pour plus d’informations, consultez [Terminer l’Assistant](../../integration-services/import-export-data/complete-the-wizard-sql-server-import-and-export-wizard.md).  
 
## <a name="see-also"></a>Voir aussi  
[Enregistrer des packages](../../integration-services/save-packages.md)  
[Exécuter des packages Integration Services (SSIS)](../../integration-services/packages/run-integration-services-ssis-packages.md)  
[SQL Server Integration Services](../../integration-services/sql-server-integration-services.md)
 
 
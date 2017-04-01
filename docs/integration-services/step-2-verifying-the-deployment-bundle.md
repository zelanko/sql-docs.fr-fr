---
title: "&#201;tape 2 : V&#233;rification de l&#39;application de d&#233;ploiement | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 6c13f5c9-c75e-4e52-94dc-2d2db2c578fe
caps.latest.revision: 18
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
---
# &#201;tape 2 : V&#233;rification de l&#39;application de d&#233;ploiement
Dans la leçon 1, vous avez créé le projet Didacticiel de déploiement et ajouté au projet les packages et les fichiers annexes ; dans la tâche précédente, vous avez créé un utilitaire de déploiement pour le projet.  
  
Dans cette tâche, vous allez vérifier le contenu de l'application de déploiement. Elle correspond au dossier que vous allez copier sur l'ordinateur de destination et qui servira à installer des packages. Si vous avez utilisé la valeur par défaut—bin\Deployment—comme emplacement de l'utilitaire de déploiement, l'application de déploiement correspond au dossier Bin\Deployment dans le dossier du didacticiel de déploiement du projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
### Pour vérifier le contenu de l'application de déploiement  
  
1.  Localisez le dossier bin\Deployment sur votre ordinateur.  
  
2.  Vérifiez que les fichiers suivants sont présents :  
  
    -   DataTransfer.dtsx  
  
    -   datatransferconfig.dtsconfig  
  
    -   Deployment Tutorial.SSISDeploymentManifest  
  
    -   LoadXMLData.dtsx  
  
    -   loadxmldataconfig.dtsconfig  
  
    -   NewCustomers.txt  
  
    -   orders.xml  
  
    -   orders.xsd  
  
    -   Lisezmoi.txt  
  
3.  Cliquez avec le bouton droit sur Deployment Tutorial.SSISDeploymentManifest, pointez sur **Ouvrir avec**, puis cliquez sur **Internet Explorer**. Vous pouvez aussi faire appel à un éditeur de texte tel que le Bloc-notes pour ouvrir le fichier. Le code XML du fichier doit être le suivant :  
  
    `<?xml version="1.0"?><DTSDeploymentManifest GeneratedBy="Domain\UserName" GeneratedFromProjectName="Deployment Tutorial" GeneratedDate="2006-02-24T13:29:02.6537669-08:00" AllowConfigurationChanges="true"><Package>DataTransfer.dtsx</Package><Package>LoadXMLData.dtsx</Package><ConfigurationFile>datatransferconfig.dtsconfig</ConfigurationFile><ConfigurationFile>loadxmldataconfig.dtsconfig</ConfigurationFile><MiscellaneousFile>Readme.txt</MiscellaneousFile><MiscellaneousFile>orders.xml</MiscellaneousFile><MiscellaneousFile>NewCustomers.txt</MiscellaneousFile><MiscellaneousFile>orders.xsd</MiscellaneousFile></DTSDeploymentManifest>`  
  
4.  Vérifiez que la valeur de l’attribut **AllowConfigurationChanges** est **true** et que le code XML inclut un élément **Package** pour chacun des deux packages, un élément **MiscellaneousFile** pour chacun des quatre fichiers non-package et un élément **ConfigurationFile** pour chacun des deux fichiers de configuration XML.  
  
5.  Quittez Internet Explorer ou l'éditeur de texte.  
  
## Leçon suivante  
[Leçon 3 : Installer des packages SSIS](../integration-services/lesson-3-install-ssis-packages.md)  
  
  
  

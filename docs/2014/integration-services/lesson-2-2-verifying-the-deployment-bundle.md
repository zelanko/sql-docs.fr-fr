---
title: 'Étape 2 : Vérification du Bundle de déploiement | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 6c13f5c9-c75e-4e52-94dc-2d2db2c578fe
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 127044042eed7f082b6f1f7ba7ae6918232ba9ff
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58378087"
---
# <a name="step-2-verifying-the-deployment-bundle"></a>Étape 2 : Vérification de l'application de déploiement
  Dans la leçon 1, vous avez créé le projet Didacticiel de déploiement et ajouté au projet les packages et les fichiers annexes ; dans la tâche précédente, vous avez créé un utilitaire de déploiement pour le projet.  
  
 Dans cette tâche, vous allez vérifier le contenu de l'application de déploiement. Elle correspond au dossier que vous allez copier sur l'ordinateur de destination et qui servira à installer des packages. Si vous avez utilisé la valeur par défaut, bin\Deployment, comme emplacement de l’utilitaire de déploiement, l’application de déploiement correspond au dossier Bin\Deployment dans le dossier du tutoriel de déploiement du projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
### <a name="to-verify-the-content-of-deployment-bundle"></a>Pour vérifier le contenu de l'application de déploiement  
  
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
  
4.  Vérifiez que la valeur de la `AllowConfigurationChanges` attribut est **true** et le code XML inclut un `Package` pour chacun des deux packages, un `MiscellaneousFile` pour chacun des quatre fichiers non-package et un `ConfigurationFile` élément pour chacune des deux fichiers de configuration XML.  
  
5.  Quittez Internet Explorer ou l'éditeur de texte.  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 3 : Installation des Packages](../integration-services/lesson-3-install-ssis-package.md)  
  
![Icône Integration Services (petite)](media/dts-16.gif "icône Integration Services (petite)")**rester jusqu'à la Date avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visitez la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
  

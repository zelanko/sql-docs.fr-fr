---
description: 'Leçon 5-3 : Modifier la valeur de configuration de la propriété Directory'
title: 'Étape 3 : Modifier la valeur de configuration de la propriété Directory | Microsoft Docs'
ms.custom: ''
ms.date: 01/08/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: ba2a091f-361c-4331-afe2-53b465164c36
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2a727a5c8d709e982582c26cff8d6cf09eb44ccc
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "88345695"
---
# <a name="lesson-5-3-modify-the-directory-property-configuration-value"></a>Leçon 5-3 : Modifier la valeur de configuration de la propriété Directory

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]



Dans cette tâche, vous modifiez le paramètre de configuration, stocké dans le fichier **SSISTutorial.dtsConfig**, pour définir la propriété **Value** de la variable de niveau package `User::varFolderName`. Cette variable met à jour la propriété **Directory** du conteneur de boucles Foreach. La valeur modifiée pointe sur le dossier **New Sample Data** que vous avez créé dans la tâche précédente. Après avoir modifié le paramètre de configuration et exécuté le package, la propriété **Directory** est mise à jour à partir de la variable dans le fichier de configuration. Auparavant, la valeur de la propriété **Directory** faisait partie du package.  
  
## <a name="modify-the-configuration-setting-of-the-directory-property"></a>Modifier le paramètre de configuration de la propriété Directory  
  
1.  Dans le Bloc-notes ou dans tout autre éditeur de texte, recherchez et ouvrez le fichier de configuration **SSISTutorial.dtsConfig** que vous avez créé à l’aide de l’Assistant Configuration de package au cours de la tâche précédente.  
  
2.  Modifiez la valeur de l’élément **ConfiguredValue** pour qu’elle corresponde au chemin du dossier **New Sample Data** que vous avez créé dans la tâche précédente. N’encadrez pas le chemin de guillemets. Si le dossier **New Sample Data** se trouve à la racine de votre lecteur (par exemple, **C:\\**), le code XML mis à jour doit être semblable à l’exemple suivant :  
  
    ```
    <?xml version="1.0"?>
    <DTSConfiguration>
      <DTSConfigurationHeading>
        <DTSConfigurationFileInfo GeneratedBy="DOMAIN\UserName" GeneratedFromPackageName="Lesson 5" GeneratedFromPackageID="{F4475E73-59E3-478F-8EB2-B10AFEE1D3FA}" GeneratedDate="6/10/2018 8:16:50 AM"/>
      </DTSConfigurationHeading>
      <Configuration ConfiguredType="Property" 
          Path="\Package.Variables[User::varFolderName].Properties[Value]" ValueType="String">
        <ConfiguredValue>C:\New Sample Data</ConfiguredValue>
      </Configuration>
    </DTSConfiguration>  
    ```

    Les informations d’en-tête, **GeneratedBy**, **GeneratedFromPackageID** et **GeneratedDate** sont différentes dans votre fichier. L’élément à noter est l’élément **Configuration** . La propriété **Value** de la variable `User::varFolderName` contient maintenant **C:\New Sample Data**.  
  
3.  Enregistrez les modifications, puis fermez l'éditeur de texte.  
  
## <a name="go-to-next-task"></a>Passer à la tâche suivante  
[Étape 4 : Tester le package de la leçon 5](../integration-services/lesson-5-4-testing-the-lesson-5-tutorial-package.md)  
  
  
  

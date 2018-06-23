---
title: Gestionnaire de connexions de fichiers multiples | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- folders [Integration Services], connections
- files [Integration Services], connections
- Multiple Files connection manager
- connection managers [Integration Services], Multiple Files
- connections [Integration Services], files
- multiple file connections
ms.assetid: 10bdc56e-c5cd-4ddb-b2f7-375fe57fe8b2
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 22fe47c60aadc0f5014b7aef2171399f8ea0d22a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051999"
---
# <a name="multiple-files-connection-manager"></a>Gestionnaire de connexions de fichiers multiples
  Un gestionnaire de connexions de fichiers multiples permet à un package de référencer des fichiers et dossiers existants ou de créer des fichiers ou dossiers au moment de l'exécution.  
  
> [!NOTE]  
>  Les tâches et composants de flux de données de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] n'utilisent pas le gestionnaire de connexions de fichiers multiples. Toutefois, vous pouvez utiliser ce gestionnaire de connexions dans la tâche de script ou le composant Script. Pour plus d’informations sur l’utilisation des gestionnaires de connexions avec la tâche de script, consultez [Connexion à des sources de données dans la tâche de script](../extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md). Pour plus d’informations sur l’utilisation des gestionnaires de connexions dans le composant Script, consultez [connexion aux Sources de données dans le composant Script] (.. / extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md.  
  
## <a name="usage-types-of-the-multiple-files-connection-manager"></a>Types d'utilisations du gestionnaire de connexions de fichiers multiples  
 La propriété `FileUsageType` du gestionnaire de connexions de fichiers multiples indique la manière dont la connexion est utilisée. Le gestionnaire de connexions de fichiers multiples permet de créer des fichiers, de créer des dossiers, d'utiliser des fichiers existants et d'utiliser des dossiers existants.  
  
 Le tableau suivant répertorie les valeurs de `FileUsageType`.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**0**|Le gestionnaire de connexions de fichiers multiples utilise un fichier existant.|  
|**1**|Le gestionnaire de connexions de fichiers multiples crée un fichier.|  
|**2**|Le gestionnaire de connexions de fichiers multiples utilise un dossier existant.|  
|**3**|Le gestionnaire de connexions de fichiers multiples crée un dossier.|  
  
## <a name="configuration-of-the-multiple-files-connection-manager"></a>Configuration du gestionnaire de connexions de fichiers multiples  
 Lorsque vous ajoutez un gestionnaire de connexions de fichiers multiples à un package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée un gestionnaire de connexions qui sera converti en connexion de fichiers multiples au moment de l'exécution, définit les propriétés de la connexion de fichiers multiples et ajoute la connexion de fichiers multiples à la collection `Connections` du package.  
  
 Le `ConnectionManagerType` du Gestionnaire de connexions est définie sur `MULTIFILE`.  
  
 Vous pouvez configurer un gestionnaire de connexions de fichiers multiples de plusieurs manières :  
  
-   Spécifiez le type d'utilisation des fichiers et des dossiers.  
  
-   Spécifiez les fichiers et les dossiers.  
  
-   Si vous utilisez plusieurs fichiers ou dossiers, indiquez l'ordre d'accès des fichiers et dossiers.  
  
 Si le gestionnaire de connexions de fichiers multiples référence plusieurs fichiers et dossiers, les chemins d'accès aux fichiers et dossiers sont séparés par une barre verticale (|). La propriété `ConnectionString` du gestionnaire de connexions utilise le format suivant :  
  
 \<*chemin*>|\<*chemin*>  
  
 Vous pouvez également spécifier plusieurs fichiers ou dossiers en utilisant des caractères génériques. Par exemple, pour la référence de lecteur de tous les fichiers de texte sur le C, la valeur de la `ConnectionString` propriété peut être définie sur C:\\*.txt.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , consultez [Référence de l’interface utilisateur de la boîte de dialogue Ajouter un gestionnaire de connexions de fichiers](add-file-connection-manager-dialog-box-ui-reference.md).  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programme, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programme](../building-packages-programmatically/adding-connections-programmatically.md).  
  
  
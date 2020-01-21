---
title: Gestionnaire de connexions Excel | Microsoft Docs
ms.date: 04/02/2018
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.custom: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.excelconnection.f1
helpviewer_keywords:
- files [Integration Services], connections
- connections [Integration Services], Excel
- Excel [Integration Services]
- connection managers [Integration Services], Excel
ms.assetid: 667419f2-74fb-4b50-b963-9197d1368cda
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f9ce3042bedd23c5ee173b1df7669a09cce35351
ms.sourcegitcommit: 365a919e3f0b0c14440522e950b57a109c00a249
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75831751"
---
# <a name="excel-connection-manager"></a>Gestionnaire de connexions Excel

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Un gestionnaire de connexions Excel permet à un package de se connecter à un fichier de classeur [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel. La source et la destination Excel incluses dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilisent le gestionnaire de connexions Excel.  
 
> [!IMPORTANT]
> Pour obtenir des informations détaillées sur la connexion à des fichiers Excel, et sur les limitations et les problèmes connus liés au chargement de données depuis ou vers des fichiers Excel, consultez [Charger des données depuis ou vers Excel avec SQL Server Integration Services (SSIS)](../load-data-to-from-excel-with-ssis.md).

 Quand vous ajoutez un gestionnaire de connexions Excel à un package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée un gestionnaire de connexions qui est converti en connexion Excel au moment de l’exécution, définit les propriétés du gestionnaire de connexions et ajoute le gestionnaire de connexions à la collection **Connections** du package.  
  
 La propriété **ConnectionManagerType** du gestionnaire de connexions a pour valeur **EXCEL**.  
  
## <a name="configure-the-excel-connection-manager"></a>Configurer le gestionnaire de connexions Excel  
 Vous pouvez configurer le gestionnaire de connexions Excel de plusieurs manières :  
  
-   Spécifiez le chemin d'accès du fichier Excel.  
  
-   Spécifiez la version d'Excel utilisée pour créer le fichier.  
  
-   Indiquez si la première ligne de données dans les feuilles de calcul ou plages sélectionnées contient des noms de colonnes.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , consultez [Éditeur du gestionnaire de connexions Excel](../../integration-services/connection-manager/excel-connection-manager-editor.md).  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programme](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="excel-connection-manager-editor"></a>Éditeur du gestionnaire de connexions Excel
  La boîte de dialogue **Éditeur du gestionnaire de connexions Excel** vous permet d'ajouter une connexion à un classeur [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] existant ou nouveau.  
  
### <a name="options"></a>Options  
 **Chemin de fichier Excel**  
 Tapez le chemin et le nom d’un fichier de classeur Excel existant ou nouveau.  
   
 **Parcourir**  
 Utilisez la boîte de dialogue **Ouvrir** pour accéder au dossier contenant le fichier Excel existant ou au dossier où vous souhaitez créer le fichier.  
  
 **Version Excel**  
 Spécifiez la version de Microsoft Excel qui a été utilisée pour créer le fichier.  
  
 **La première ligne possède des noms de colonnes**  
 Permet de spécifier si la première ligne de données dans la feuille de calcul sélectionnée contient les noms des colonnes. La valeur par défaut de cette option est **True**.  

## <a name="solution-to-import-data-with-mixed-data-types-from-excel"></a>Solution pour importer des données de types mixtes à partir d'Excel

Si vous utilisez des données contenant des types de données mixtes, par défaut, le pilote Excel lit les 8 premières lignes (configurées par la clé de registre **TypeGuessRows**). Sur la base des 8 premières lignes de données, le pilote Excel essaie de deviner le type de données de chaque colonne. Par exemple, si votre source de données Excel comporte des chiffres et du texte dans une colonne, si les 8 premières lignes contiennent des chiffres, le pilote peut déterminer, sur la base de ces 8 premières lignes, que les données de la colonne sont de type entier. Dans ce cas, SSIS ignore les valeurs de texte et les importe comme des données NULL dans la destination.

Pour résoudre ce problème, vous pouvez essayer l'une des solutions suivantes :

* Remplacez le type de colonne Excel par **Texte** dans le fichier Excel.
* Ajoutez la propriété étendue IMEX à la chaîne de connexion pour remplacer le comportement par défaut du pilote. Lorsque vous ajoutez la propriété étendue « ;IMEX=1 » à la fin de la chaîne de connexion, Excel traite toutes les données comme du texte. Voir l’exemple suivant :
    
  ```ACE OLEDB connection string:
  Provider=Microsoft.ACE.OLEDB.12.0;Data Source=C:\ExcelFileName.xlsx;Extended Properties="EXCEL 12.0 XML;HDR=YES;IMEX=1";
  ```

   Pour que cette solution fonctionne de manière fiable, vous devrez peut-être également modifier les paramètres du registre. Le fichier main.cmd se présente comme suit :
  
   ```cmd
   reg add "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Office\12.0\Access Connectivity Engine\Engines\Excel" /t REG_DWORD /v TypeGuessRows /d 0 /f
   reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\12.0\Access Connectivity Engine\Engines\Excel" /t REG_DWORD /v TypeGuessRows /d 0 /f
   reg add "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Office\14.0\Access Connectivity Engine\Engines\Excel" /t REG_DWORD /v TypeGuessRows /d 0 /f
   reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\14.0\Access Connectivity Engine\Engines\Excel" /t REG_DWORD /v TypeGuessRows /d 0 /f
   reg add "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Office\15.0\Access Connectivity Engine\Engines\Excel" /t REG_DWORD /v TypeGuessRows /d 0 /f
   reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\15.0\Access Connectivity Engine\Engines\Excel" /t REG_DWORD /v TypeGuessRows /d 0 /f
   reg add "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Office\16.0\Access Connectivity Engine\Engines\Excel" /t REG_DWORD /v TypeGuessRows /d 0 /f
   reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\16.0\Access Connectivity Engine\Engines\Excel" /t REG_DWORD /v TypeGuessRows /d 0 /f
   ```

* Enregistrez le fichier au format CSV et modifiez le package SSIS pour qu’il prenne en charge une importation CSV.

## <a name="related-tasks"></a>Tâches associées  
[Charger des données depuis ou vers Excel avec SQL Server Integration Services (SSIS)](../load-data-to-from-excel-with-ssis.md)  
[Source Excel](../data-flow/excel-source.md)  
[Destination Excel](../data-flow/excel-destination.md)

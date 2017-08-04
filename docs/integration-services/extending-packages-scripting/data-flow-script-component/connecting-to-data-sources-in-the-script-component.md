---
title: "Connexion aux Sources de données dans le composant Script | Documents Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Script component [Integration Services], connecting to data sources
ms.assetid: 96de63ab-ff48-4e7e-89e0-ffd6a89c63b6
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e2accca553f1bd9c536076fd0bbcebbff0ff2c42
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="connecting-to-data-sources-in-the-script-component"></a>Connexion aux sources de données dans le composant Script
  Un gestionnaire de connexions est une unité pratique qui encapsule et stocke les informations requises pour se connecter à une source de données d'un type particulier. Pour plus d’informations, consultez [Connexions Integration Services &#40;SSIS&#41;](../../../integration-services/connection-manager/integration-services-ssis-connections.md).  
  
 Vous proposer des gestionnaires de connexions existant pour l’accès par le script personnalisé dans le composant source ou de destination en cliquant sur le **ajouter** et **supprimer** des boutons de la **gestionnaires de connexions** page de la **éditeur de Transformation de Script**. Toutefois, vous devez écrire votre propre code personnalisé pour charger ou enregistrer vos données et éventuellement ouvrir et fermer la connexion à la source de données. Pour plus d’informations sur la **gestionnaires de connexions** page de la **éditeur de Transformation de Script**, consultez [configuration du composant Script dans l’éditeur de composant Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md) et [éditeur de Transformation de Script &#40; Page gestionnaires de connexions &#41; ](../../../integration-services/data-flow/transformations/script-transformation-editor-connection-managers-page.md).  
  
 Le composant Script crée un **connexions** classe de collection dans le **ComponentWrapper** élément de projet qui contient un accesseur fortement typé pour chaque gestionnaire de connexions qui a le même nom que le Gestionnaire de connexions lui-même. Cette collection est exposée via le **connexions** propriété de la **ScriptMain** classe. La propriété de l'accesseur renvoie une référence au gestionnaire de connexions sous forme d'instance de l'objet <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSConnectionManager100>. Par exemple, si vous avez ajouté un gestionnaire de connexion nommé `MyADONETConnection` dans la page Gestionnaires de connexions de la boîte de dialogue, vous pouvez obtenir une référence à ce dernier dans votre script en ajoutant le code suivant :  
  
 `Dim myADONETConnectionManager As IDTSConnectionManager100 = _`  
  
 `Me.Connections.MyADONETConnection`  
  
> [!NOTE]  
>  Vous devez connaître le type de connexion qui est retournée par le Gestionnaire de connexions avant d’appeler **AcquireConnection**. Étant donné que la tâche de Script a **Option Strict** activé, vous devez caster la connexion, ce qui est retournée en tant que type **objet**, pour le type de connexion approprié avant que vous puissiez l’utiliser.  
  
 Ensuite, vous appelez le **AcquireConnection** méthode du Gestionnaire de connexions spécifique pour obtenir les informations requises pour se connecter à la source de données ou la connexion sous-jacente. Par exemple, vous obtenez une référence à la **System.Data.SqlConnection** encapsulé par un gestionnaire de connexions ADO.NET en utilisant le code suivant :  
  
 `Dim myADOConnection As SqlConnection = _`  
  
 `CType(MyADONETConnectionManager.AcquireConnection(Nothing), SqlConnection)`  
  
 Par opposition, le même appel d'un gestionnaire de connexions de fichier plat retourne uniquement le chemin d'accès et le nom de fichier de la source de données.  
  
 `Dim myFlatFile As String = _`  
  
 `CType(MyFlatFileConnectionManager.AcquireConnection(Nothing), String)`  
  
 Vous devez alors fournir ce chemin d’accès et nom de fichier à un **System.IO.StreamReader** ou **Streamwriter** pour lire ou écrire les données dans le fichier plat.  
  
> [!IMPORTANT]  
>  Lorsque vous écrivez du code managé dans un composant de Script, vous ne pouvez pas appeler la méthode AcquireConnection de connexion gestionnaires qui retournent des objets non managés, tels que le Gestionnaire de connexions OLE DB et le Gestionnaire de connexions Excel. Toutefois, vous pouvez lire la propriété ConnectionString de ces gestionnaires de connexions et vous connecter à la source de données directement dans votre code à l’aide de la chaîne de connexion d’un OLEDB **connexion** à partir de la **System.Data.OleDb** espace de noms.  
>   
>  Si vous avez besoin d’appeler la méthode AcquireConnection d’un gestionnaire de connexions qui retourne un objet non managé, utilisez un gestionnaire de connexions ADO.NET. Lorsque vous configurez le gestionnaire de connexions ADO.NET afin d'utiliser un fournisseur OLE DB, il se connecte en utilisant le fournisseur de données .NET Framework pour OLE DB. Dans ce cas, la méthode AcquireConnection retourne un **System.Data.OleDb.OleDbConnection** au lieu d’un objet non managé. Pour configurer un gestionnaire de connexions ADO.NET pour une utilisation avec une source de données Excel, sélectionnez le fournisseur Microsoft OLE DB pour Jet, spécifiez un classeur Excel, puis entrez `Excel 8.0` (pour Excel 97 et versions ultérieures) comme valeur de **propriétés étendues** sur la **tous les** page de la **Gestionnaire de connexions** boîte de dialogue.  
  
 Pour plus d’informations sur l’utilisation des gestionnaires de connexions avec le composant script, consultez [création d’une Source avec le composant Script](../../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md) et [création d’une Destination avec le composant Script](../../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services &#40; SSIS &#41; Connexions](../../../integration-services/connection-manager/integration-services-ssis-connections.md)   
 [Créer des gestionnaires de connexions](http://msdn.microsoft.com/library/6ca317b8-0061-4d9d-b830-ee8c21268345)  
  
  

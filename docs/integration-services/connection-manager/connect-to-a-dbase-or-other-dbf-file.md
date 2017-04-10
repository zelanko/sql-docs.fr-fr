---
title: "Se connecter &#224; un fichier&#160;dBASE ou &#224; un autre fichier&#160;DBF | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "connexion à des fichiers DBF"
  - "dBase (fichiers)"
  - "DBF (fichiers)"
ms.assetid: b0e8c831-9f96-475c-82a4-4f5b02692752
caps.latest.revision: 16
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 16
---
# Se connecter &#224; un fichier&#160;dBASE ou &#224; un autre fichier&#160;DBF
  Vous pouvez vous connecter à un fichier dBASE ou à un autre fichier de base de données .DBF dans un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] en utilisant un gestionnaire de connexions OLE DB et en sélectionnant le fournisseur Microsoft OLE DB pour Jet 4.0.  
  
> [!NOTE]  
>  L'Assistant Importation et Exportation SQL Server disponible dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge l'importation à partir des fichiers dBASE ou d'autres fichiers DBF, ni l'exportation vers ces derniers. Vous pouvez faire appel à Microsoft Access ou Microsoft Excel pour importer les données de fichiers DBF dans une base de données Access ou des feuilles de calcul Excel, puis utiliser l'Assistant Importation et Exportation SQL Server.  
  
### Pour configurer un gestionnaire de connexions en vue de vous connecter à un fichier dBASE ou à un autre fichier DBF  
  
1.  Ajoutez un nouveau gestionnaire de connexions OLE DB au package. Pour plus d’informations, consultez [Ajouter, supprimer ou partager un gestionnaire de connexions dans un package](../Topic/Add,%20Delete,%20or%20Share%20a%20Connection%20Manager%20in%20a%20Package.md).  
  
2.  Dans la page **Connexion** de la boîte de dialogue **Gestionnaire de connexions**, choisissez le fournisseur OLE DB natif\OLE DB pour Microsoft Jet 4.0 en tant que **Fournisseur**.  
  
3.  Lorsque vous utilisez des fichiers DBF, le dossier représente la base de données tandis que les fichiers DBF représentent les tables. La zone de texte **Nom du fichier de la base de données** doit donc contenir le chemin du dossier où se trouve le fichier DBF, sans inclure le nom de fichier lui-même. Vous pouvez taper ou coller directement le chemin d’un dossier, ou utiliser le bouton **Parcourir** pour sélectionner votre fichier DBF, puis supprimer le nom de fichier à la fin du chemin du dossier.  
  
4.  Dans la page **Tout** de la boîte de dialogue **Gestionnaire de connexions**, entrez, selon vos besoins, **dBASE III**, **dBASE IV** ou **dBASE 5.0** en tant que valeur de Propriétés étendues.  
  
5.  Cliquez sur **Tester la connexion** pour valider les valeurs que vous avez entrées. Le message « Le test de la connexion a réussi. » doit s'afficher. Cliquez sur **OK** pour fermer le message.  
  
6.  Cliquez sur **OK** pour enregistrer la configuration du gestionnaire de connexions.  
  
7.  Pour utiliser le gestionnaire de connexions dans le flux de données du package, sélectionnez une source ou une destination OLE DB et configurez-la pour vous servir du gestionnaire de connexions que vous avez créé au cours des étapes précédentes.  
  
## Voir aussi  
 [Gestionnaire de connexions OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md)  
  
  
---
title: "Destination de fichier plat | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.flatfiledest.f1"
helpviewer_keywords: 
  - "fichiers plats"
  - "Destination de fichier plat"
  - "écriture de fichier texte [Integration Services]"
  - "destinations [Integration Services], fichier plat"
ms.assetid: e0d6e356-8db4-48aa-ba66-029397f98f61
caps.latest.revision: 49
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 49
---
# Destination de fichier plat
  La destination de fichier plat écrit des données dans un fichier texte. Le fichier texte peut se présenter dans un format délimité, à largeur fixe, à largeur fixe avec séparateur de ligne ou en drapeau à droite.  
  
 Vous pouvez configurer la destination de fichier plat de plusieurs manières :  
  
-   Fournissez un bloc de texte qui est inséré dans le fichier avant l'écriture des données. Le texte peut fournir des informations telles que des en-têtes de colonnes.  
  
-   Spécifiez s'il faut remplacer des données dans un fichier de destination qui porte le même nom.  
  
 Cette destination utilise un gestionnaire de connexions de fichier plat pour accéder au fichier texte. En définissant les propriétés du gestionnaire de connexions de fichier plat utilisé par la destination de fichier plat, vous pouvez spécifier la façon dont elle met en forme et écrit le fichier texte. Lors de la configuration du gestionnaire de connexions de fichier plat, vous spécifiez des informations sur le fichier et sur chacune de ses colonnes. Par exemple, vous spécifiez les caractères qui délimitent les colonnes et les lignes du fichier, ainsi que le type de données et la longueur de chaque colonne. Pour plus d'informations, consultez [Flat File Connection Manager](../../integration-services/connection-manager/flat-file-connection-manager.md).  
  
 La destination de fichier plat inclut la propriété personnalisée Header. La propriété peut être mise à jour par une expression de propriété lors du chargement du package. Pour plus d’informations, consultez [Expressions Integration Services &#40;SSIS&#41;](../../integration-services/expressions/integration-services-ssis-expressions.md), [Expressions de propriété dans des packages](../../integration-services/expressions/use-property-expressions-in-packages.md) et [Propriétés personnalisées des fichiers plats](../../integration-services/data-flow/flat-file-custom-properties.md).  
  
 Cette destination possède une sortie. Elle ne prend pas en charge de sortie d'erreur.  
  
## Configuration de la destination de fichier plat  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans la boîte de dialogue **Éditeur de source de fichier plat**, cliquez sur l’une des rubriques suivantes :  
  
-   [Éditeur de destination de fichier plat &#40;page Gestionnaire de connexions&#41;](../../integration-services/data-flow/flat-file-destination-editor-connection-manager-page.md)  
  
-   [Éditeur de destination de fichier plat &#40;page Mappages&#41;](../../integration-services/data-flow/flat-file-destination-editor-mappings-page.md)  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../Topic/Common%20Properties.md)  
  
-   [Propriétés personnalisées des fichiers plats](../../integration-services/data-flow/flat-file-custom-properties.md)  
  
## Tâches associées  
 Pour plus d’informations sur la définition des propriétés d’un composant de flux de données, consultez [Définir les propriétés d’un composant de flux de données](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## Voir aussi  
 [Source de fichier plat](../../integration-services/data-flow/flat-file-source.md)   
 [Flux de données](../../integration-services/data-flow/data-flow.md)  
  
  
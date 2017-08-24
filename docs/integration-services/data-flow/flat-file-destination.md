---
title: Plat de Destination de fichier | Documents Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.flatfiledest.f1
helpviewer_keywords:
- flat files
- Flat File destination
- text file writing [Integration Services]
- destinations [Integration Services], Flat File
ms.assetid: e0d6e356-8db4-48aa-ba66-029397f98f61
caps.latest.revision: 49
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 78a0ec526f83dcab8d7358ef5a51f1f6ccfd0a04
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="flat-file-destination"></a>Destination de fichier plat
  La destination de fichier plat écrit des données dans un fichier texte. Le fichier texte peut se présenter dans un format délimité, à largeur fixe, à largeur fixe avec séparateur de ligne ou en drapeau à droite.  
  
 Vous pouvez configurer la destination de fichier plat de plusieurs manières :  
  
-   Fournissez un bloc de texte qui est inséré dans le fichier avant l'écriture des données. Le texte peut fournir des informations telles que des en-têtes de colonnes.  
  
-   Spécifiez s'il faut remplacer des données dans un fichier de destination qui porte le même nom.  
  
 Cette destination utilise un gestionnaire de connexions de fichier plat pour accéder au fichier texte. En définissant les propriétés du gestionnaire de connexions de fichier plat utilisé par la destination de fichier plat, vous pouvez spécifier la façon dont elle met en forme et écrit le fichier texte. Lors de la configuration du gestionnaire de connexions de fichier plat, vous spécifiez des informations sur le fichier et sur chacune de ses colonnes. Par exemple, vous spécifiez les caractères qui délimitent les colonnes et les lignes du fichier, ainsi que le type de données et la longueur de chaque colonne. Pour plus d'informations, consultez [Flat File Connection Manager](../../integration-services/connection-manager/flat-file-connection-manager.md).  
  
 La destination de fichier plat inclut la propriété personnalisée Header. La propriété peut être mise à jour par une expression de propriété lors du chargement du package. Pour plus d’informations, consultez [Expressions Integration Services &#40;SSIS&#41;](../../integration-services/expressions/integration-services-ssis-expressions.md), [Expressions de propriété dans des packages](../../integration-services/expressions/use-property-expressions-in-packages.md) et [Propriétés personnalisées des fichiers plats](../../integration-services/data-flow/flat-file-custom-properties.md).  
  
 Cette destination possède une sortie. Elle ne prend pas en charge de sortie d'erreur.  
  
## <a name="configuration-of-the-flat-file-destination"></a>Configuration de la destination de fichier plat  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans la boîte de dialogue **Éditeur de source de fichier plat** , cliquez sur l’une des rubriques suivantes :  
  
-   [Éditeur de destination de fichier plat &#40;page Gestionnaire de connexions&#41;](../../integration-services/data-flow/flat-file-destination-editor-connection-manager-page.md)  
  
-   [Éditeur de destination de fichier plat &#40;page Mappages&#41;](../../integration-services/data-flow/flat-file-destination-editor-mappings-page.md)  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programme, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Propriétés personnalisées des fichiers plats](../../integration-services/data-flow/flat-file-custom-properties.md)  
  
## <a name="related-tasks"></a>Tâches associées  
 Pour plus d’informations sur la définition des propriétés d’un composant de flux de données, consultez [Définir les propriétés d’un composant de flux de données](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Source de fichier plat](../../integration-services/data-flow/flat-file-source.md)   
 [Flux de données](../../integration-services/data-flow/data-flow.md)  
  
  

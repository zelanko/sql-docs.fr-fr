---
title: Création de procédures stockées | Documents Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- registering assemblies
- database assemblies [Analysis Services]
- server assemblies [Analysis Services]
- stored procedures [Analysis Services], creating
- assemblies [Analysis Services]
ms.assetid: a12ff02f-6d0b-4488-9846-3609fc0d0554
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1efb84c34892b411ebd66285a68f9e5dc8cef66b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142371"
---
# <a name="creating-stored-procedures"></a>Création de procédures stockées
  Toutes les procédures stockées doivent être associées à une classe CLR (Common Language Runtime) ou COM (Component Object Model) pour pouvoir être utilisées. La classe doit être installée sur le serveur, généralement sous la forme d’un [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX® bibliothèque de liens dynamiques (DLL) et enregistré en tant qu’assembly sur le serveur ou dans un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] base de données.  
  
 Les procédures stockées sont enregistrées sur le serveur ou dans une base de données. Les procédures stockées enregistrées sur le serveur peuvent être appelées à partir de n'importe quel contexte de requête. Les procédures stockées enregistrées dans la base de données sont uniquement accessibles si le contexte de base de données est la base de données dans laquelle la procédure stockée est définie. Si les fonctions d'un assembly appellent les fonctions d'un autre assembly, vous devez enregistrer les deux assemblys dans le même contexte (serveur ou base de données). Pour un serveur ou un déploiement [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] base de données sur un serveur, vous pouvez utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour enregistrer un assembly. Pour un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vous pouvez utiliser le Concepteur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour enregistrer un assembly dans le projet.  
  
> [!IMPORTANT]  
>  Les assemblys COM peuvent présenter un risque pour la sécurité. En raison de ce risque et d'autres considérations, les assemblys COM ont été déconseillés dans [!INCLUDE[ssASversion10](../../includes/ssasversion10-md.md)]. Les assemblys COM peuvent ne pas être pris en charge dans les versions ultérieures.  
  
## <a name="registering-a-server-assembly"></a>Enregistrement d'un assembly de serveur  
 Dans l'Explorateur d'objets de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], les assemblys de serveur sont répertoriés dans le dossier Assemblies d'une instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Les assemblys de serveur peuvent contenir à la fois des assemblys .NET (CLR) et des bibliothèques COM.  
  
### <a name="to-create-a-server-assembly"></a>Pour créer un assembly de serveur  
  
1.  Développez l’instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans l’Explorateur d’objets, cliquez sur le **assemblys** dossier, puis cliquez sur **nouvel Assembly**. Cela permet d’afficher le **enregistrer l’Assembly de serveur** boîte de dialogue.  
  
2.  Pour **Type** spécifier le type d’assembly :  
  
    -   Pour une DLL en code managé (CLR), spécifiez Assembly .NET.  
  
    -   Pour un DLL COM () le code natif, spécifiez DLL COM.  
  
3.  Pour **nom de fichier**, spécifiez la DLL contenant les procédures stockées.  
  
4.  Pour **nom de l’Assembly**, spécifiez un nom pour l’assembly.  
  
5.  S’il s’agit d’une version debug de la bibliothèque que vous vous apprêtez à utiliser pour déboguer les procédures stockées, sélectionnez le **inclure les informations de débogage** case à cocher. Pour plus d’informations sur le débogage des procédures stockées, consultez [le débogage des procédures stockées](debugging-stored-procedures.md).  
  
6.  Vous pouvez cliquer sur **OK** pour inscrire l’assembly immédiatement ou sur la barre d’outils de boîte de dialogue, vous pouvez cliquer sur une commande sur le **Script** menu créer un script de l’action d’enregistrement dans une fenêtre de requête, un fichier ou le Presse-papiers.  
  
 Après avoir inscrit un assembly de serveur, vous pouvez le configurer en cliquant sur l’assembly dans l’Explorateur d’objets, puis sur **propriétés**.  
  
## <a name="registering-a-database-assembly-on-the-server"></a>Enregistrement d'un assembly de base de données sur le serveur  
 Dans l'Explorateur d'objets de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], les assemblys de base de données sont répertoriés dans le dossier Assemblies d'une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Les assemblys de base de données peuvent contenir à la fois des assemblys .NET (CLR) et des bibliothèques COM.  
  
### <a name="to-create-a-database-assembly-on-a-server"></a>Pour créer un assembly de base de données sur un serveur  
  
1.  Développez l’instance de la [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans l’Explorateur d’objets de base de données, cliquez sur le **assemblys** dossier, puis cliquez sur **nouvel Assembly**. Cela permet d’afficher le **enregistrer l’Assembly de base de données** boîte de dialogue.  
  
2.  Pour **Type** spécifier le type d’assembly :  
  
    -   Pour une DLL en code managé (CLR), spécifiez Assembly .NET.  
  
    -   Pour une DLL en code natif (COM), spécifiez DLL COM.  
  
3.  Pour **nom de fichier**, spécifiez la DLL contenant les procédures stockées.  
  
4.  Pour **nom de l’Assembly**, spécifiez un nom pour l’assembly.  
  
5.  S’il s’agit d’une version debug de la bibliothèque que vous vous apprêtez à utiliser pour déboguer les procédures stockées, sélectionnez le **inclure les informations de débogage** case à cocher. Pour plus d’informations sur le débogage des procédures stockées, consultez [le débogage des procédures stockées](debugging-stored-procedures.md).  
  
6.  Vous pouvez cliquer sur **OK** pour inscrire l’assembly immédiatement ou sur la barre d’outils de boîte de dialogue, vous pouvez cliquer sur une commande sur le **Script** menu créer un script de l’action d’enregistrement dans une fenêtre de requête, un fichier ou le Presse-papiers.  
  
 Après avoir inscrit un assembly de base de données, vous pouvez le configurer en cliquant sur l’assembly dans l’Explorateur d’objets, puis sur **propriétés**.  
  
## <a name="registering-a-database-assembly-in-a-project"></a>Enregistrement d'un assembly de base de données dans un projet  
 Dans l'Explorateur de solutions de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], les assemblys de base de données sont répertoriés dans le dossier Assemblies d'un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Les assemblys de base de données peuvent contenir à la fois des assemblys .NET (CLR) et des bibliothèques COM.  
  
### <a name="to-create-a-database-assembly-in-an-analysis-service-project"></a>Pour créer un assembly de base de données dans un projet Analysis Service  
  
1.  Développez l’instance de la [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans l’Explorateur d’objets de base de données, cliquez sur le **assemblys** dossier, puis cliquez sur **nouvelle référence d’Assembly**. Cela permet d’afficher le **ajouter une référence** boîte de dialogue. Le **.NET** onglet de la **ajouter une référence** boîte de dialogue répertorie les assemblys .NET (CLR) existants, alors que le **projets** onglet répertorie les projets.  
  
2.  Vous pouvez cliquez sur un composant existant ou un projet, puis sur **ajouter** pour l’ajouter à la [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projet. Pour ajouter une référence à une DLL COM, cliquez sur le **Parcourir** onglet pour rechercher le fichier. Le **projets et composants sélectionnés** liste affiche le nom, un type, une version et un emplacement pour chaque composant que vous ajoutez au projet.  
  
3.  Lorsque vous avez fini de sélectionner les composants à ajouter, cliquez sur **OK** pour les ajouter à la [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projet.  
  
## <a name="script-format-for-an-assembly"></a>Mise en forme du script pour un assembly  
 Il est relativement simple d'enregistrer un assembly .NET. Un assembly .NET est ajouté à une base de données au format binaire à l'aide du format suivant :  
  
```  
<Create>  
   <ObjectDefinition>  
      <Assembly>  
         <Files>  
            <File>  
               <Name>filename</Name>  
               <Type>filetype</Type>  
               <Data>  
                  <Block>binarydatablock</Block>  
                  <Block>binarydatablock</Block>  
                  ...  
               </Data>  
            </File>  
         </Files>  
         <PermissionSet>PermissionSet</PermissionSet>  
      </Assembly>  
   <ObjectDefinition>  
</Create>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des assemblys de modèle multidimensionnel](../multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Définition de procédures stockées](defining-stored-procedures.md)  
  
  
---
title: Création de procédures stockées | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- registering assemblies
- database assemblies [Analysis Services]
- server assemblies [Analysis Services]
- stored procedures [Analysis Services], creating
- assemblies [Analysis Services]
ms.assetid: a12ff02f-6d0b-4488-9846-3609fc0d0554
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7beb77adf595b055a6c1e4a7543b428a06ce7640
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62703095"
---
# <a name="creating-stored-procedures"></a>Création de procédures stockées
  Toutes les procédures stockées doivent être associées à une classe CLR (Common Language Runtime) ou COM (Component Object Model) pour pouvoir être utilisées. La classe doit être installée sur le serveur, généralement sous la forme d’une [!INCLUDE[msCoName](../../includes/msconame-md.md)] bibliothèque de liens dynamiques (DLL)® ActiveX, et inscrite en tant qu’assembly sur le [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] serveur ou dans une base de données.  
  
 Les procédures stockées sont enregistrées sur le serveur ou dans une base de données. Les procédures stockées enregistrées sur le serveur peuvent être appelées à partir de n'importe quel contexte de requête. Les procédures stockées enregistrées dans la base de données sont uniquement accessibles si le contexte de base de données est la base de données dans laquelle la procédure stockée est définie. Si les fonctions d'un assembly appellent les fonctions d'un autre assembly, vous devez enregistrer les deux assemblys dans le même contexte (serveur ou base de données). Pour un serveur ou une base [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de données déployée sur un serveur, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] vous pouvez utiliser pour inscrire un assembly. Pour un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vous pouvez utiliser le Concepteur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour enregistrer un assembly dans le projet.  
  
> [!IMPORTANT]  
>  Les assemblys COM peuvent présenter un risque pour la sécurité. En raison de ce risque et d'autres considérations, les assemblys COM ont été déconseillés dans [!INCLUDE[ssASversion10](../../includes/ssasversion10-md.md)]. Les assemblys COM peuvent ne pas être pris en charge dans les versions ultérieures.  
  
## <a name="registering-a-server-assembly"></a>Enregistrement d'un assembly de serveur  
 Dans l'Explorateur d'objets de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], les assemblys de serveur sont répertoriés dans le dossier Assemblies d'une instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Les assemblys de serveur peuvent contenir à la fois des assemblys .NET (CLR) et des bibliothèques COM.  
  
### <a name="to-create-a-server-assembly"></a>Pour créer un assembly de serveur  
  
1.  Développez l’instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de dans l’Explorateur d’objets, cliquez avec le bouton droit sur le dossier **assemblys** , puis cliquez sur **nouvel assembly**. La boîte de dialogue **inscrire un assembly de serveur** s’affiche.  
  
2.  Pour **type** , spécifiez le type d’assembly :  
  
    -   Pour une DLL en code managé (CLR), spécifiez Assembly .NET.  
  
    -   Pour une DLL de code natif (COM), spécifiez la DLL COM.  
  
3.  Pour **nom de fichier**, spécifiez la dll contenant les procédures stockées.  
  
4.  Pour **nom de l’assembly**, spécifiez un nom pour l’assembly.  
  
5.  S’il s’agit d’une version de débogage de la bibliothèque que vous allez utiliser pour déboguer des procédures stockées, activez la case à cocher **inclure les informations de débogage** . Pour plus d’informations sur le débogage des procédures stockées, consultez [débogage de procédures stockées](debugging-stored-procedures.md).  
  
6.  Vous pouvez cliquer sur **OK** pour inscrire l’assembly immédiatement, ou dans la barre d’outils de la boîte de dialogue, vous pouvez cliquer sur une commande du menu **script** pour générer un script de l’action d’inscription dans une fenêtre de requête, un fichier ou le presse-papiers.  
  
 Une fois que vous avez inscrit un assembly de serveur, vous pouvez le configurer en cliquant avec le bouton droit sur l’assembly dans l’Explorateur d’objets, puis en cliquant sur **Propriétés**.  
  
## <a name="registering-a-database-assembly-on-the-server"></a>Enregistrement d'un assembly de base de données sur le serveur  
 Dans l'Explorateur d'objets de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], les assemblys de base de données sont répertoriés dans le dossier Assemblies d'une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Les assemblys de base de données peuvent contenir à la fois des assemblys .NET (CLR) et des bibliothèques COM.  
  
### <a name="to-create-a-database-assembly-on-a-server"></a>Pour créer un assembly de base de données sur un serveur  
  
1.  Développez l’instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de la base de données dans l’Explorateur d’objets, cliquez avec le bouton droit sur le dossier **assemblys** , puis cliquez sur **nouvel assembly**. La boîte **de dialogue inscrire l’assembly de base de données** s’affiche.  
  
2.  Pour **type** , spécifiez le type d’assembly :  
  
    -   Pour une DLL en code managé (CLR), spécifiez Assembly .NET.  
  
    -   Pour une DLL en code natif (COM), spécifiez DLL COM.  
  
3.  Pour **nom de fichier**, spécifiez la dll contenant les procédures stockées.  
  
4.  Pour **nom de l’assembly**, spécifiez un nom pour l’assembly.  
  
5.  S’il s’agit d’une version de débogage de la bibliothèque que vous allez utiliser pour déboguer des procédures stockées, activez la case à cocher **inclure les informations de débogage** . Pour plus d’informations sur le débogage des procédures stockées, consultez [débogage de procédures stockées](debugging-stored-procedures.md).  
  
6.  Vous pouvez cliquer sur **OK** pour inscrire l’assembly immédiatement, ou dans la barre d’outils de la boîte de dialogue, vous pouvez cliquer sur une commande du menu **script** pour générer un script de l’action d’inscription dans une fenêtre de requête, un fichier ou le presse-papiers.  
  
 Une fois que vous avez inscrit un assembly de base de données, vous pouvez le configurer en cliquant avec le bouton droit sur l’assembly dans l’Explorateur d’objets, puis en cliquant sur **Propriétés**.  
  
## <a name="registering-a-database-assembly-in-a-project"></a>Enregistrement d'un assembly de base de données dans un projet  
 Dans l'Explorateur de solutions de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], les assemblys de base de données sont répertoriés dans le dossier Assemblies d'un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Les assemblys de base de données peuvent contenir à la fois des assemblys .NET (CLR) et des bibliothèques COM.  
  
### <a name="to-create-a-database-assembly-in-an-analysis-service-project"></a>Pour créer un assembly de base de données dans un projet Analysis Service  
  
1.  Développez l’instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de la base de données dans l’Explorateur d’objets, cliquez avec le bouton droit sur le dossier **assemblys** , puis cliquez sur **nouvelle référence d’assembly**. La boîte de dialogue **Ajouter une référence** s’affiche. L’onglet **.net** de la boîte de dialogue **Ajouter une référence** répertorie les assemblys .net (CLR) existants, tandis que l’onglet **projets** répertorie les projets.  
  
2.  Vous pouvez cliquer sur un composant ou un projet existant, puis cliquer sur **Ajouter** pour l' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ajouter au projet. Pour ajouter une référence à une DLL COM, cliquez sur l’onglet **Parcourir** pour rechercher le fichier. La liste **projets et composants sélectionnés** affiche le nom, le type, la version et l’emplacement de chaque composant que vous ajoutez au projet.  
  
3.  Lorsque vous avez terminé de sélectionner les composants à ajouter, cliquez sur **OK** pour les [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ajouter au projet.  
  
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
 [Gestion des assemblys de modèles multidimensionnels](../multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Définition de procédures stockées](defining-stored-procedures.md)  
  
  

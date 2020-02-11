---
title: Définir des calculs Time Intelligence à l’aide de l’Assistant Business Intelligence | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- period over period growth [Analysis Services]
- parallel period comparisons [Analysis Services]
- Business Intelligence enhancements [Analysis Services], time intelligence
- time views [Analysis Services]
- hierarchies [Analysis Services], time
- time periods [Analysis Services]
- moving averages
- time [Analysis Services]
- period to date [Analysis Services]
- calculations [Analysis Services], time
- time hierarchies [Analysis Services]
- time intelligence [Analysis Services]
ms.assetid: be36e8fc-f46e-4553-8623-b27d695c330b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c665c894a4e0bb3691c483a8d8bab084ac2fa276
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66075433"
---
# <a name="define-time-intelligence-calculations-using-the-business-intelligence-wizard"></a>Définir des calculs Time Intelligence à l'aide de l'Assistant Business Intelligence
  L'amélioration Time Intelligence est une amélioration de cube qui ajoute des calculs de temps (ou vues temporelles) à une hiérarchie sélectionnée. Cette amélioration prend en charge les catégories de calculs suivantes :  
  
-   Cumul périodique jusqu'à ce jour  
  
-   Croissance d'une période sur l'autre  
  
-   Moyennes mobiles  
  
-   Comparaisons de périodes parallèles  
  
 Vous pouvez appliquer Time Intelligence aux cubes qui possèdent une dimension de temps (une dimension de temps est une dimension dont la propriété `Type` a la valeur `Time`). En outre, la propriété `Type` des attributs de temps de cette dimension doit également être définie sur le paramètre approprié (comme Années ou Mois). La propriété `Type` de la dimension et de ses attributs sera correctement définie si vous utilisez l'Assistant Dimension pour créer la dimension de temps.  
  
 Pour ajouter Time Intelligence à un cube, utilisez l’Assistant Business Intelligence, puis sélectionnez l’option **Exécuter l’Assistant Time Intelligence** dans la page **Choisir des améliorations** . Cet Assistant vous guide ensuite dans la procédure à suivre pour sélectionner la hiérarchie à laquelle vous voulez ajouter Time Intelligence et pour spécifier les membres de la hiérarchie auxquels vous voulez appliquer cette fonctionnalité. Dans la dernière page de l’Assistant, vous pouvez voir les modifications qui seront apportées à [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] la base de données afin d’ajouter l’intelligence temporelle sélectionnée.  
  
## <a name="selecting-a-time-hierarchy"></a>Sélection d'une hiérarchie de temps  
 Dans la page **Choisir la hiérarchie cible et les calculs** , sélectionnez la hiérarchie de temps à laquelle vous souhaitez appliquer Time Intelligence. Vous pouvez appliquer Time Intelligence à une seule hiérarchie de temps à chaque fois que vous exécutez l'Assistant Business Intelligence. Si vous voulez appliquer cette amélioration à plusieurs hiérarchies de temps, vous devez exécuter à nouveau l'Assistant.  
  
 Après avoir sélectionné une hiérarchie de temps, dans la liste **Calculs de temps disponibles** , vous sélectionnez les calculs qui s’appliquent à la hiérarchie. Les calculs disponibles dépendent des niveaux de la hiérarchie et du paramètre de la propriété `Type` de l'attribut pour chaque niveau. Par exemple, une hiérarchie Années, contrairement à une hiérarchie Trimestres, prend en charge Cumul annuel jusqu'à ce jour et Croissance d'une année sur l'autre.  
  
> [!NOTE]  
>  Le fichier modèle Timeintelligence.xml définit les calculs de temps qui figurent dans la liste **Calculs de temps disponibles**. Si les calculs disponibles ne correspondent pas à vos besoins, vous pouvez soit modifier les calculs existants, soit ajouter de nouveaux calculs au fichier Timeintelligence.xml.  
  
> [!TIP]  
>  Pour afficher la description d'un calcul, utilisez les flèches vers le haut et vers le bas pour mettre ce calcul en surbrillance.  
  
## <a name="apply-time-views-to-members"></a>Appliquer des vues temporelles à des membres  
 Dans la page **Définir l’étendue des calculs** , spécifiez les membres auxquels les nouvelles vues temporelles s’appliquent. Vous pouvez appliquer les nouvelles vues temporelles à l'un des objets suivants :  
  
-   **Membres d’une dimension de compte** Dans la page **définir l’étendue des calculs** , la liste **mesures disponibles** comprend les dimensions de compte. Une dimension de comptes est une dimension dont la propriété `Type` a la valeur `Accounts`. Si vous avez une dimension de comptes, mais qu’elle n’apparaît pas dans la liste **Mesures disponibles** , vous pouvez utiliser l’Assistant Business Intelligence pour appliquer l’intelligence comptable à cette dimension. Pour plus d’informations, consultez [Ajouter de l’intelligence comptable à une dimension](bi-wizard-add-account-intelligence-to-a-dimension.md).  
  
-   **Mesures** Au lieu de spécifier une dimension de compte, vous pouvez spécifier les mesures auxquelles s’appliquent les vues temporelles. Dans ce cas, sélectionnez les vues auxquelles s'appliquent les calculs de temps sélectionnés. Par exemple, l'actif et le passif sont des données de cumul annuel jusqu'à ce jour ; par conséquent, vous n'allez pas appliquer un calcul Cumul annuel jusqu'à ce jour aux mesures d'actif ou de passif.  
  
## <a name="viewing-the-time-intelligence-enhancement"></a>Affichage de l'amélioration Time Intelligence  
 Dans la page finale de l’Assistant Business Intelligence, vous pouvez voir les modifications qui vont être apportées à la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . En ajoutant l'amélioration Time Intelligence, l'Assistant modifiera la dimension de temps sélectionnée, la vue de source de données correspondante et le cube correspondant comme cela est décrit dans le tableau suivant.  
  
|Object|Modifier|  
|------------|------------|  
|Dimension de temps|Ajoute un attribut pour chaque calcul (ou vue).|  
|Vue de source de données|Ajoute une colonne calculée dans la table de temps pour chaque attribut ajouté à la dimension de temps.|  
|Cube|Ajoute un membre calculé qui définit le code MDX (Multidimensional Expressions) pour effectuer le calcul.|  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des membres calculés](create-calculated-members.md)  
  
  

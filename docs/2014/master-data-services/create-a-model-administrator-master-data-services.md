---
title: Créer un administrateur de modèle (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- administrators [Master Data Services], creating
ms.assetid: dae17afc-3b39-490e-b51f-2d8da26d429e
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 06f5acf3bf8c9c4f8df7282934c99b38480a1bd3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044744"
---
# <a name="create-a-model-administrator-master-data-services"></a>Créer un administrateur de modèle (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], créer un administrateur de modèle lorsque vous souhaitez un groupe ou à l’utilisateur **mise à jour** autorisation à tous les objets dans un ou plusieurs modèles.  
  
> [!TIP]  
>  Pour simplifier l'administration, créez un groupe Windows ou local et configurez-le comme un administrateur de modèle. Vous pouvez ensuite ajouter et supprimer des utilisateurs dans le groupe sans accéder à l'interface utilisateur de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Autorisations d'accès** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-create-a-model-administrator"></a>Pour créer un administrateur de modèle  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Autorisations d'accès**.  
  
2.  Dans la page **Utilisateurs** ou **Groupes** , sélectionnez la ligne de l'utilisateur ou du groupe à modifier.  
  
3.  Cliquez sur **Modifier l'utilisateur sélectionné**.  
  
4.  Cliquez sur l'onglet **Modèles** .  
  
5.  Dans la liste **Modèle** , sélectionnez éventuellement un modèle.  
  
6.  Cliquez sur **Modifier**.  
  
7.  Cliquez sur le modèle auquel vous souhaitez affecter une autorisation.  
  
8.  Dans le menu, sélectionnez **mise à jour**.  
  
9. Effectuez les étapes 7 et 8 pour chaque modèle que vous souhaitez que le groupe ou l'utilisateur administre.  
  
10. Cliquez sur **Enregistrer**.  
  
## <a name="remarks"></a>Notes  
 N'affectez pas d'autres autorisations à des objets modèle ou membres de hiérarchie. Si vous le faites, l’utilisateur n’est plus un administrateur et ne peut pas afficher le modèle dans une zone fonctionnelle autre que **Explorer**.  
  
 Il existe une exception : si l’utilisateur a **mise à jour** une autorisation attribuée à une hiérarchie **racine** sur la **membres de hiérarchie** onglet, l’utilisateur est toujours considérée comme un modèle administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Les administrateurs &#40;Master Data Services&#41;](administrators-master-data-services.md)   
 [Affecter des autorisations d’objet de modèle &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Affecter des autorisations de membre de hiérarchie &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)   
 [Autorisations d’objet de modèle &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Autorisations des membres de hiérarchie &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
---
title: Enregistrer un Package en tant que modèle de Package | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- reusing packages
- templates [Integration Services]
ms.assetid: efe66cec-3933-4f6e-8d35-fe3d300de66c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 76349c0ca91f24a6d8d7942a89eb9683a91b573d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66056341"
---
# <a name="save-a-package-as-a-package-template"></a>Enregistrer un package en tant que modèle de package
  Cette rubrique indique comment désigner et utiliser des packages personnalisés comme modèles lorsque que vous créez de nouveaux packages Integration Services dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Par défaut, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] utilise un modèle de package qui crée un package vide lorsque vous ajoutez un nouveau package à un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Vous ne pouvez pas remplacer ce modèle par défaut, mais vous pouvez en ajouter de nouveaux.  
  
 Vous pouvez désigner plusieurs packages à utiliser comme modèles. Avant de pouvoir implémenter de nouveaux packages personnalisés comme modèles, vous devez créer les packages.  
  
 Lorsque vous créez un package en utilisant des packages personnalisés comme modèles, les nouveaux packages portent le même nom et le même GUID que le modèle. Pour différencier les packages, il faut mettre à jour la valeur de la propriété `Name` et générer un nouveau GUID pour la propriété `ID`. Pour plus d’informations, consultez [Créer des packages dans les outils de données SQL Server](create-packages-in-sql-server-data-tools.md) et [Définir les propriétés d’un package](set-package-properties.md).  
  
### <a name="to-designate-a-custom-package-as-a-package-template"></a>Pour désigner un package personnalisé comme modèle de package  
  
1.  Dans le système de fichiers, localisez le package que vous souhaitez utiliser comme modèle.  
  
2.  Copiez le package dans le dossier DataTransformationItems. Par défaut ce dossier se trouve dans C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies\ProjectItems\DataTransformationProject.  
  
3.  Recommencez les étapes 1 et 2 pour chaque package que vous souhaitez utiliser comme modèle.  
  
### <a name="to-use-a-custom-package-as-a-package-template"></a>Pour utiliser un package personnalisé comme modèle de package  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] dans lequel vous souhaitez créer un package.  
  
2.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet, pointez sur **Ajouter**, puis cliquez sur **Nouvel élément**.  
  
3.  Dans la boîte de dialogue **Ajouter un nouvel élément -\<nom_projet>** , cliquez sur le package que vous voulez utiliser comme modèle.  
  
     La liste de modèles inclut le modèle de package par défaut nommé Nouveau package SSIS. L'icône de package identifie les modèles pouvant être utilisés comme modèles de packages.  
  
4.  Cliquez sur **Ajouter**.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des packages dans SQL Server Data Tools](create-packages-in-sql-server-data-tools.md)   
 [Packages Integration Services &#40;SSIS&#41;](../../2014/integration-services/integration-services-ssis-packages.md)  
  
  

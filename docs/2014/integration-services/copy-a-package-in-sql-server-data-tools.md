---
title: Copier un package dans SQL Server Data Tools | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], copying
- copying packages
- regenerating package GUID
- updating package properties
ms.assetid: 03edc659-e76d-48c0-a749-5f1899b6b507
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 023ffdb16c16c54093190a370c3d8a52c068104b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48229319"
---
# <a name="copy-a-package-in-sql-server-data-tools"></a>Copier un package dans les outils de données SQL Server
  Cette rubrique explique comment créer un package [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] en copiant un package existant, et comment mettre à jour les propriétés `Name` et `GUID` du nouveau package.  
  
### <a name="to-copy-a-package"></a>Pour copier un package  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] qui contient le package que vous voulez copier.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package.  
  
3.  Vérifiez soit que le package à copier est sélectionné dans l'Explorateur de solutions, soit que l'onglet du concepteur SSIS qui contient le package est l'onglet actif.  
  
4.  Dans le menu **Fichier**, cliquez sur **Enregistrer \<nom_package> sous**.  
  
    > [!NOTE]  
    >  Le package doit être ouvert dans le concepteur SSIS pour que l’option **Enregistrer sous** apparaisse dans le menu **Fichier** .  
  
5.  Le cas échéant, accédez à un autre dossier.  
  
6.  Mettez à jour le nom du fichier de package. Veillez à conserver l'extension de fichier .dtsx.  
  
7.  Cliquez sur **Enregistrer**.  
  
8.  À l'invite, déterminez si vous voulez mettre à jour le nom de l'objet de package afin qu'il corresponde au nom de fichier. Si vous cliquez sur **Oui**, le `Name` propriété du package est mis à jour. Le nouveau package est ajouté au projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] et ouvert dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
9. Le cas échéant, cliquez sur l’arrière-plan de l’onglet **Flux de contrôle** , puis cliquez sur **Propriétés**.  
  
10. Dans la fenêtre Propriétés, cliquez sur la valeur de la propriété ID, puis cliquez sur **\<Générer un nouvel ID>** dans la liste déroulante.  
  
11. Dans le menu **Fichier** , cliquez sur **Enregistrer les éléments sélectionnés** pour enregistrer le nouveau package.  
  
## <a name="see-also"></a>Voir aussi  
 [Enregistrer une copie d’un Package](../../2014/integration-services/save-a-copy-of-a-package.md)   
 [Créer des packages dans SQL Server Data Tools](create-packages-in-sql-server-data-tools.md)   
 [Packages Integration Services &#40;SSIS&#41;](../../2014/integration-services/integration-services-ssis-packages.md)  
  
  

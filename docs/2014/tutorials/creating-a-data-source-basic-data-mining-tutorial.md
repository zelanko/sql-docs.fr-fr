---
title: Création d’une Source de données (didacticiel d’exploration de données de base) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: d7107c32-69ed-49a8-9b6e-32753eebf42c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0e216aa5da4ef837da632ba83d4cf6e14edb40b1
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53376451"
---
# <a name="creating-a-data-source-basic-data-mining-tutorial"></a>Création d'une source de données (Didacticiel sur l'exploration de données de base)
  Un *source de données* est une connexion de données qui est enregistrée et gérée dans votre projet et déployée sur votre [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] base de données. La source de données contient les noms du serveur et de la base de données où vos données sources résident, en plus des éventuelles propriétés de connexion requises.  
  
> [!IMPORTANT]  
>  Le nom de la base de données est [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]. Si vous n’avez pas déjà installé cette base de données, consultez le [Microsoft SQL Sample Databases](https://go.microsoft.com/fwlink/?LinkId=88417) page.  
  
### <a name="to-create-a-data-source"></a>Pour créer une source de données  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit le **des Sources de données** dossier et sélectionnez **nouvelle Source de données**.  
  
2.  Sur le **Bienvenue dans l’Assistant Source de données** , cliquez sur **suivant**.  
  
3.  Sur le **sélectionner la méthode de définition de la connexion** , cliquez sur **New** pour ajouter une connexion à la [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] base de données.  
  
4.  Dans le **fournisseur** liste **Gestionnaire de connexions**, sélectionnez **Native OLE DB\SQL Server Native Client 11.0**.  
  
5.  Dans le **nom du serveur** , tapez ou sélectionnez le nom du serveur sur lequel vous avez installé [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)].  
  
     Par exemple, tapez **localhost** si la base de données est hébergée sur le serveur local.  
  
6.  Dans le **connectez-vous au serveur** groupe, sélectionnez **utiliser l’authentification Windows**.  
  
    > [!IMPORTANT]  
    >  Dans la mesure du possible, les implémenteurs doivent utiliser l'authentification Windows car elle fournit une méthode d'authentification plus sécurisée que l'authentification SQL Server. Cependant, l'authentification SQL Server est fournie dans le but d'assurer la compatibilité ascendante. Pour plus d’informations sur les méthodes d’authentification, consultez [Configuration du moteur de base de données - l’approvisionnement de comptes](../../2014/sql-server/install/database-engine-configuration-account-provisioning.md).  
  
7.  Dans le **sélectionner ou entrer un nom de base de données** , sélectionnez [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] puis cliquez sur **OK**.  
  
8.  Cliquer sur **Suivant**.  
  
9. Sur le **les informations d’emprunt d’identité** , cliquez sur **utiliser le compte de service**, puis cliquez sur **suivant**.  
  
     Sur le **fin de l’Assistant** page, notez que, par défaut, la source de données est nommée Adventure Works DW 2012.  
  
10. Cliquez sur **Terminer**.  
  
     La nouvelle source de données, Adventure Works DW 2012, apparaît dans le **des Sources de données** dossier dans l’Explorateur de solutions.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Vue de Source de création d’une données &#40;didacticiel d’exploration de données de base&#41;](../../2014/tutorials/creating-a-data-source-view-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>Tâche précédente de la leçon  
 [Création d’une analyse de projet Services &#40;didacticiel d’exploration de données de base&#41;](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Créer une source de données &#40;SSAS Multidimensionnel&#41;](../analysis-services/multidimensional-models/create-a-data-source-ssas-multidimensional.md)   
 [Définition d’une Source de données](../analysis-services/lesson-1-2-defining-a-data-source.md)   
 [Définir les options d’emprunt d’identité &#40;SSAS - Multidimensionnel&#41;](../analysis-services/multidimensional-models/set-impersonation-options-ssas-multidimensional.md)  
  
  

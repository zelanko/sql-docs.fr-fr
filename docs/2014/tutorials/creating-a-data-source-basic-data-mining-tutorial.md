---
title: Création d’une source de données (didacticiel sur l’exploration de données de base) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d7107c32-69ed-49a8-9b6e-32753eebf42c
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3f85320a99c901a2fd71c9048750825569559099
ms.sourcegitcommit: f5807ced6df55dfa78ccf402217551a7a3b44764
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69494026"
---
# <a name="creating-a-data-source-basic-data-mining-tutorial"></a>Création d'une source de données (Didacticiel sur l'exploration de données de base)
  Une *source de données* est une connexion de données qui est enregistrée et gérée dans votre projet et [!INCLUDE[msCoName](../includes/msconame-md.md)] déployée dans votre [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] base de données. La source de données contient les noms du serveur et de la base de données où vos données sources résident, en plus des éventuelles propriétés de connexion requises.  
  
> [!IMPORTANT]  
>  Le nom de la base de données est [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]. Si vous n’avez pas encore installé cette base de données, consultez la page [exemples de bases de données Microsoft SQL](https://go.microsoft.com/fwlink/?LinkId=88417) .  
  
### <a name="to-create-a-data-source"></a>Pour créer une source de données  
  
1.  Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le dossier **sources de données** et sélectionnez **nouvelle source de données**.  
  
2.  Sur la page **Bienvenue dans l’Assistant source de données** , cliquez sur **suivant**.  
  
3.  Sur la page **Sélectionner la méthode de définition de la connexion** , cliquez sur **nouveau** pour ajouter une [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] connexion à la base de données.  
  
4.  Dans la liste **fournisseur** du **Gestionnaire de connexions**, sélectionnez **Native OLE DB\SQL Server Native Client 11,0**.  
  
5.  Dans la zone **nom du serveur** , tapez ou sélectionnez le nom du serveur sur lequel vous avez [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]installé.  
  
     Par exemple, tapez **localhost** si la base de données est hébergée sur le serveur local.  
  
6.  Dans le **Journal sur le** groupe de serveurs, sélectionnez **utiliser l’authentification Windows**.  
  
    > [!IMPORTANT]  
    >  Dans la mesure du possible, les implémenteurs doivent utiliser l'authentification Windows car elle fournit une méthode d'authentification plus sécurisée que l'authentification SQL Server. Cependant, l'authentification SQL Server est fournie dans le but d'assurer la compatibilité ascendante. Pour plus d’informations sur les méthodes d’authentification, consultez [configuration de moteur de base de données-approvisionnement de comptes](../../2014/sql-server/install/database-engine-configuration-account-provisioning.md).  
  
7.  Dans la liste **Sélectionner ou entrer un nom de base de données** , sélectionnez [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] , puis cliquez sur **OK**.  
  
8.  Cliquez sur **Suivant**.  
  
9. Sur la page **informations d’emprunt d’identité** , cliquez sur **utiliser le compte de service**, puis cliquez sur **suivant**.  
  
     Dans la page **fin de l’Assistant** , Notez que, par défaut, la source de données est nommée Adventure Works DW 2012.  
  
10. Cliquez sur **Terminer**.  
  
     La nouvelle source de données, Adventure Works DW 2012, apparaît dans le dossier **sources de données** de Explorateur de solutions.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Création d’une vue &#40;de source de données didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/creating-a-data-source-view-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>Tâche précédente de la leçon  
 [Didacticiel de création d' &#40;un Analysis Services projet de base d’exploration de données&#41;](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Créer une source de données &#40;SSAS Multidimensionnel&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/create-a-data-source-ssas-multidimensional)   
 [Définition d’une source de données](../analysis-services/lesson-1-2-defining-a-data-source.md)   
 [Définir les options d’emprunt d’identité &#40;SSAS - Multidimensionnel&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/set-impersonation-options-ssas-multidimensional)  
  
  

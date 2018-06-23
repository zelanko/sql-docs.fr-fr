---
title: Guide pratique pour créer et modifier un service CDC | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1b3d47a5-dc89-482d-bbc7-fff04f194c43
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 04d25e8628ccb0de237615c0e422c5fc2f7af957
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041415"
---
# <a name="how-to-create-and-edit-a-cdc-service"></a>Procédure : créer et modifier un service de capture de données modifiées
  Ces procédures décrivent comment créer et modifier un service de capture de données modifiées Oracle dans la console de configuration du service de capture de données modifiées.  
  
 Cette procédure requiert un utilisateur Windows avec des privilèges d'administrateur sur l'ordinateur sur lequel le service de capture de données modifiées Oracle est configuré.  
  
### <a name="to-create-a-new-cdc-service"></a>Pour créer un service de capture de données modifiées  
  
1.  Dans le menu **Démarrer** , sélectionnez **Configuration du service de capture de données modifiées pour Oracle**.  
  
2.  Dans le volet gauche, cliquez avec le bouton droit sur Services de capture de données modifiées locaux, puis sélectionnez Nouveau service.  
  
     Vous pouvez également cliquer sur **Nouveau service** dans le volet **Actions** .  
  
3.  Tapez ou entrez les informations nécessaires dans la boîte de dialogue Nouveau service de capture de données modifiées Oracle. Pour plus d'informations sur la façon d'entrer des informations dans la boîte de dialogue Nouveau service de capture de données modifiées Oracle, consultez [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md) .  
  
     La connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spécifiée dans la boîte de dialogue Nouveau service de capture de données modifiées Oracle est utilisée par le service de capture de données modifiées Oracle lorsqu'il s'exécute. Cette connexion doit être membre du rôle serveur fixe public ; aucun autre privilège n'est nécessaire. Une fois que de nouvelles instances Oracle CDC sont ajoutées, cette connexion a un accès **db_owner** aux bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC.  
  
4.  Lorsque vous avez terminé d'entrer les informations nécessaires, cliquez sur **OK**.  
  
     Pour créer la définition de service Windows de capture de données modifiées Oracle, le programme doit disposer d'un accès de mise à jour à la base de données MSXDBCDC dans l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] associée. Lorsque vous cliquez sur **OK**, une boîte de dialogue vous invite à entrer une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec un accès de mise à jour à la base de données MSXDBCDC.  
  
     Pour plus d'informations sur les données que vous devez taper dans la boîte de dialogue Connexion à SQL Server, consultez [Connection to SQL Server](connection-to-sql-server.md).  
  
5.  Cliquez sur **OK** pour fermer la boîte de dialogue Nouveau service de capture de données modifiées Oracle.  
  
### <a name="to-edit-a-cdc-service"></a>Pour modifier un service de capture de données modifiées  
  
1.  Dans le menu **Démarrer** , sélectionnez **Configuration du service de capture de données modifiées pour Oracle**.  
  
2.  Dans le volet gauche, sélectionnez **Services de capture de données modifiées locaux** , cliquez avec le bouton droit sur le service local que vous souhaitez modifier, puis sélectionnez **Propriétés**.  
  
     Vous pouvez également sélectionner le service que vous utilisez dans le volet central, puis dans le volet **Actions** , cliquer sur **Propriétés**.  
  
3.  Tapez ou entrez les informations nécessaires dans la boîte de dialogue de propriétés du service de capture de données modifiées Oracle. Pour plus d'informations sur la façon d'entrer des informations dans la boîte de dialogue de propriétés du service de capture de données modifiées Oracle, consultez [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md) .  
  
4.  Lorsque vous avez terminé d'entrer les informations nécessaires, cliquez sur **OK**; la boîte de dialogue Connexion à SQL Server s'ouvre.  
  
     Lorsqu'une connexion sans autorisation d'écriture sur la base de données MSXDBDCDC tente de créer une instance Oracle CDC un message d'erreur s'affiche. Cliquez sur **OK** dans cette boîte de dialogue pour afficher la boîte de dialogue Connexion à SQL Server. Dans cette boîte de dialogue, vous devez entrer les informations d’identification pour une connexion qui dispose de l’autorisation en écriture sur la base de données MSXDBCDC, telle que le rôle de base de données **db_owner** .  
  
     Pour plus d'informations sur les données que vous devez taper dans la boîte de dialogue Connexion à SQL Server, consultez [Connection to SQL Server](connection-to-sql-server.md).  
  
5.  Cliquez sur **OK** dans la boîte de dialogue Connexion à Oracle. Les deux boîtes de dialogue se ferment et le service est mis à jour et inscrit.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteur de Capture de données modifiées pour Oracle par Attunity](change-data-capture-designer-for-oracle-by-attunity.md)   
 [Créer et modifier un service CDC Oracle](create-and-edit-an-oracle-cdc-service.md)  
  
  
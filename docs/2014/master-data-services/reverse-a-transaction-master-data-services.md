---
title: Inverser une transaction (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Master Data Services], reversing
ms.assetid: 6f7c3f07-0f64-4283-8c9c-93facd00a046
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 572a0fbe10594226a755a4f7ecb59c2e52ef6c82
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48140669"
---
# <a name="reverse-a-transaction-master-data-services"></a>Inverser une transaction (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], les administrateurs peuvent inverser une transaction lorsqu'une action doit être annulée. Les exemples de transactions sont les suivants : modifications apportées aux valeurs d'attribut, déplacements de hiérarchie ou suppressions de membres.  
  
## <a name="prerequisites"></a>Prérequis  
  
-   Vous devez avoir l’autorisation d’accéder à la zone fonctionnelle **Gestion des versions** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-reverse-a-transaction"></a>Pour inverser une transaction  
  
1.  Dans la page d’accueil de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , cliquez sur **Gestion des versions**.  
  
2.  Dans la barre de menus, cliquez sur **Transactions**.  
  
3.  Dans la page **Transactions** , dans la liste **Modèle** , sélectionnez un modèle.  
  
4.  Dans la liste **Version** , sélectionnez une version.  
  
5.  Cliquez dans la grille sur la ligne correspondant à la transaction que vous souhaitez inverser.  
  
6.  Cliquez sur **Inverser la transaction**.  
  
7.  Dans la boîte de dialogue de confirmation, cliquez sur **OK**. Une autre transaction est ajoutée à la grille pour enregistrer la transaction inversée.  
  
## <a name="see-also"></a>Voir aussi  
 [Transactions &#40;Master Data Services&#41;](../../2014/master-data-services/transactions-master-data-services.md)   
 [Réactiver un membre ou une Collection &#40;Master Data Services&#41;](../../2014/master-data-services/reactivate-a-member-or-collection-master-data-services.md)  
  
  

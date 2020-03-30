---
title: Connexion à Oracle | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- connOra
ms.assetid: 711ac7ff-5d3d-4533-80ca-d1fecdb3048f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e745a2277a01cac3dd120af241e0ae1d7575b562
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "71294748"
---
# <a name="connect-to-oracle"></a>Connexion à Oracle

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Lorsque vous ajoutez ou modifiez les tables utilisées dans l'instance de capture de données modifiées pour la première fois, vous pouvez être invité à vous connecter à la base de données Oracle. Vous devez entrer les informations d'identification d'un utilisateur Oracle qui a accès au schéma des tables à capturer. Entrez les informations suivantes dans cette boîte de dialogue :  
  
 **Authentification**  
  
 Sélectionnez l’un des suivants :  
  
-   **Authentification Windows**: sélectionnez cette option pour utiliser les informations d'identification actuelles de domaine Windows. Vous ne pouvez utiliser cette option que si la base de données Oracle est configurée pour utiliser l'authentification Windows.  
  
-   **Authentification Oracle**: si vous sélectionnez cette option, vous devez taper le **Nom d'utilisateur** et le **Mot de passe** de l'utilisateur dans la base de données Oracle à laquelle vous êtes connecté.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des tables à une instance CDC](../../integration-services/change-data-capture/add-tables-to-a-cdc-instance.md)  
  
  

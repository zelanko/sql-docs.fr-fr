---
title: Propriétés avancées de connexion | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4edfab68-7e68-45e8-a3f3-a0049ff7eb9e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: a7a5744aa2adcaab74ca09bbb962c8c69d985b79
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58379187"
---
# <a name="advanced-connection-properties"></a>Propriétés avancées de connexion
  Pour ajouter des paramètres de connexion à la chaîne de connexion, utilisez la boîte de dialogue **Propriétés avancées de connexion** .  
  
 Les paramètres de connexion supplémentaires peuvent être des paramètres de connexion ODBC pris en charge par l'instance de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que vous utilisez.  
  
 Les paramètres ajoutés à partir de la boîte de dialogue **Propriétés avancées de connexion** sont ajoutés aux paramètres sélectionnés dans la boîte de dialogue **Connexion à SQL Server** .  
  
 La dernière instance de chaque paramètre fourni remplace toutes les instances précédentes du paramètre. Les paramètres ajoutés à partir de la boîte de dialogue **Paramètres de connexion avancés** suivent et remplacent les paramètres fournis dans la boîte de dialogue **Connexion SQL Server** . Par exemple, si la boîte de dialogue **Connexion SQL Server** spécifie SERVEUR1 en tant que Nom du serveur et si la page **Paramètres de connexion supplémentaires** indique ;SERVEUR=SERVEUR2, la connexion sera établie à SERVEUR2.  
  
 Les paramètres ajoutés à partir de la boîte de dialogue **Propriétés avancées de connexion** sont transmis sous forme de texte brut.  
  
> [!IMPORTANT]  
>  N'incluez pas les informations d'identification de connexion dans la boîte de dialogue **Propriétés avancées de connexion** . Ceux-ci ne seront pas chiffrés lorsqu'ils seront transmis sur le réseau.  
  
## <a name="see-also"></a>Voir aussi  
 [Accéder à la console du concepteur CDC](access-the-cdc-designer-console.md)   
 [Connexion SQL Server pour la création d'une instance](sql-server-connection-for-instance-creation.md)  
  
  

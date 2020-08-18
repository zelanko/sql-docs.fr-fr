---
description: MSSQLSERVER_11001
title: MSSQLSERVER_11001 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
f1_keywords:
- "12001"
helpviewer_keywords:
- 11001 (Database Engine error)
ms.assetid: 53d4d63a-61e3-441f-bfe9-9d44f7a05fd4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ccd8eaeae32aeaa0e5e1d2b6b1f8f29a1ac0c43d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88336809"
---
# <a name="mssqlserver_11001"></a>MSSQLSERVER_11001
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|11001|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique||  
|Texte du message|Une erreur s'est produite lors de l'établissement d'une connexion au serveur.  Lors de la connexion à SQL Server, cet échec peut être dû au fait que les paramètres par défaut de SQL Server n'autorisent pas les connexions à distance. (fournisseur : Fournisseur TCP, erreur : 0 – Hôte inconnu) (Fournisseur de données SqlClient .Net)|  
  
## <a name="explanation"></a>Explication  
Le client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas se connecter au serveur. Cette erreur s'est peut-être produite parce que le client ne peut pas résoudre le nom du serveur ou le nom du serveur est incorrect.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Assurez-vous que vous avez entré le nom de serveur correct sur le client et que vous pouvez résoudre ce nom à partir du client. Pour vérifier la résolution du nom TCP/IP, vous pouvez exécuter la commande **ping** dans le système d’exploitation Windows.  
  
## <a name="see-also"></a>Voir aussi  
[Protocoles réseau et bibliothèques réseau](~/sql-server/install/network-protocols-and-network-libraries.md)  
[Configuration du réseau client](~/database-engine/configure-windows/client-network-configuration.md)  
[Configurer des protocoles clients](~/database-engine/configure-windows/configure-client-protocols.md)  
[Activer ou désactiver un protocole réseau de serveur](~/database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  

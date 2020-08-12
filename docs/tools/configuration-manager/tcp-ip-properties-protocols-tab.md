---
title: Propriétés de TCP/IP (onglet Protocoles)
description: Utilisez les options de l’onglet Protocoles de la boîte de dialogue Propriétés TCP/IP pour configurer l’intervalle de maintien de l’activité, l’indicateur activé et d’autres propriétés.
ms.custom: seo-lt-2019
ms.date: 08/24/2016
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- TCP/IP [SQL Server], configuration options
ms.assetid: 007638fc-3a24-4460-adbe-545ded5d6f88
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 2e9bf22b501a097e59af3bef953ffcbaa26780c1
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85880293"
---
# <a name="tcpip-properties-protocols-tab"></a>Propriétés de TCP/IP (onglet Protocoles)
[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]
  La boîte de dialogue **Propriétés de TCP/IP** permet de configurer les options du protocole TCP/IP. Cliquez sur **TCP/IP** dans le volet gauche pour afficher les configurations de chaque adresse IP dans le volet d’informations.  
  
 Pour appliquer les modifications, redémarrez Microsoft SQL Servermust.  
  
## <a name="options"></a>Options  
 **Activé**  
 Les valeurs possibles sont **Yes** et **No**.  
  
 **Keep Alive**  
 Spécifiez la fréquence (millisecondes) à laquelle les paquets de maintien d'activité sont transmis pour vérifier si l'ordinateur situé à l'extrémité distante d'une connexion est toujours disponible.  
  
 **Écouter tout**  
 Spécifiez si SQL Server doit écouter sur toutes les adresses IP liées aux cartes réseau de l'ordinateur. Si vous choisissez la valeur **No**, configurez chaque adresse IP séparément en utilisant la boîte de dialogue des propriétés de chaque adresse IP. Si vous choisissez la valeur **Yes**, les paramètres de la zone des propriétés de **IPAll** s’appliquent à toutes les adresses IP. La valeur par défaut est **Yes**.  
  
 **Aucun délai**  
 SQL Serverdoes n’implémente pas les modifications apportées à cette propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Choix d'un protocole réseau](https://msdn.microsoft.com/library/ms187892(v=sql.130).aspx)   
 [Création d’une chaîne de connexion valide à l’aide du protocole TCP/IP](creating-a-valid-connection-string-using-tcp-ip.md)  
  
  

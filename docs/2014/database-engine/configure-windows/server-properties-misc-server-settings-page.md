---
title: Propriétés du serveur (page Paramètres divers du serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.miscserversettings.f1
ms.assetid: b170c066-30cd-42dd-8d34-aa129ea09551
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: aef24f7e2a02140e776cf113089ec083d06a86aa
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84934903"
---
# <a name="server-properties-misc-server-settings-page"></a>Propriétés du serveur (page Paramètres divers du serveur)
  Utilisez cette page pour afficher ou modifier les paramètres du serveur.  
  
## <a name="options"></a>Options  
 **Langue par défaut pour l'utilisateur**  
 Spécifie la langue par défaut de toutes les nouvelles connexions.  
  
 **Autoriser les déclencheurs à déclencher d'autres déclencheurs**  
 Détermine si un déclencheur peut exécuter une action qui démarre un autre déclencheur. Lorsque cette option est désactivée, les déclencheurs ne peuvent pas être déclenchés par un autre. Lorsque cette option est activée, des déclencheurs peuvent être déclenchés par d'autres, jusqu'à 32 niveaux maximum.  
  
 **Utiliser l'Administrateur de requêtes pour empêcher les requêtes longues**  
 Spécifie une limite supérieure de durée d'exécution d'une requête. Le coût d'une requête correspond à la durée estimée (en secondes) nécessaire à l'exécution d'une requête dans une configuration matérielle donnée. Par défaut, l'Administrateur de requêtes est désactivé et toutes les requêtes peuvent être exécutées. Si cette option est activée, vous devez entrer une limite de durée dans la zone de texte qui suit. Si vous spécifiez une valeur positive et différente de zéro, l'Administrateur de requêtes n'autorise pas l'exécution de requêtes dont le coût estimé excède cette valeur.  
  
 **Interpréter une année sur deux chiffres comme comprise entre**  
 Spécifie la plage de dates de 100 ans pour interpréter les valeurs d'année à deux chiffres. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interprétera les valeurs de date à deux chiffres pour faire référence à l’année se terminant par ces chiffres figurant dans la plage spécifiée.  
  
 Spécifiez la dernière année dans la zone de droite. Lorsque la dernière année est enregistrée, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] remplit automatiquement la zone de gauche avec la première année.  
  
 **Valeurs configurées**  
 Affiche les valeurs configurées pour les options de ce volet. Si vous modifiez ces valeurs, cliquez sur **Valeurs en cours d’exécution** pour vérifier si les modifications ont été prises en compte. Si ce n'est pas le cas, vous devez redémarrer l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
 **Valeurs en cours d’exécution**  
 Affiche les valeurs en cours d'exécution pour les options de ce volet. Ces valeurs sont en lecture seule.  
  
## <a name="see-also"></a>Voir aussi  
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)  
  
  

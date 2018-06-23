---
title: common criteria compliance enabled (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- common criteria compliance
helpviewer_keywords:
- CC (common criteria) [Database Engine]
- common criteria compliance [Database Engine]
- Risidual Information Protection [Database Engine]
- RIP (Residual Information Protection)
ms.assetid: 61766eea-c450-408d-af33-fbe7ef8c9ff2
caps.latest.revision: 23
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 663ebefaa604964f9f034e0dd043cbc816977f28
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36155106"
---
# <a name="common-criteria-compliance-enabled-server-configuration-option"></a>common criteria compliance enabled (option de configuration de serveur)
  L'option common criteria compliance enabled active les éléments suivants requis pour les critères communs.  
  
|Critères|Description|  
|--------------|-----------------|  
|Protection des informations résiduelles (RIP, Residual Information Protection)|RIP nécessite qu'une allocation mémoire soit remplacée par une séquence identifiée de bits avant que la mémoire ne soit réaffectée à une nouvelle ressource. Le fait de satisfaire à la norme RIP peut contribuer à améliorer la sécurité ; cependant, le remplacement de l'allocation mémoire peut ralentir les performances. Après que l'option common criteria compliance enabled a été activée, le remplacement se produit.|  
|Possibilité de consulter des statistiques de connexion|Une fois que l'option common criteria compliance enabled a été activée, l'audit des connexions est activé. Chaque fois qu'un utilisateur parvient à se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il bénéficie d'informations sur l'heure de la dernière ouverture de session ayant abouti, l'heure de la dernière ouverture de session ayant échoué et le nombre de tentatives entre la dernière ouverture de session réussie et l'ouverture de session actuelle. Vous pouvez afficher ces statistiques de connexion en interrogeant la vue de gestion dynamique [sys.dm_exec_sessions](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) .|  
|La colonne GRANT ne doit pas remplacer la table DENY|Après que l'option de conformité des critères communs a été activée, une option DENY au niveau table est prioritaire sur une option GRANT au niveau colonne. Quand l'option n'est pas activée, une option GRANT au niveau colonne est prioritaire sur une option DENY au niveau table.|  
  
 L’option activée de conformité des critères communs est une option avancée. Les critères communs sont évalués et certifiés uniquement pour l'édition Entreprise et Datacenter. Pour connaître l'état le plus récent de la certification des critères communs, consultez le site web [Critères communs de Microsoft SQL Server](http://go.microsoft.com/fwlink/?LinkId=616319) .  
  
> [!IMPORTANT]  
>  Vous devez non seulement activer l'option common criteria compliance enabled, mais également télécharger et exécuter un script qui achève la configuration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour assurer sa conformité à la norme Critères Communs au niveau d'évaluation 4+ (EAL4+). Vous pouvez télécharger ce script à partir du site Web [Microsoft SQL Server Common Criteria (en anglais)](http://go.microsoft.com/fwlink/?LinkId=616319) .  
  
 Si vous utilisez la procédure stockée système sp_configure pour changer sa valeur, vous ne pouvez modifier l'option de conformité aux critères communs que si la valeur 1 a été attribuée à l'option show advanced options. Le paramétrage prend effet une fois le serveur redémarré. Les valeurs possibles sont 0 et 1 :  
  
-   0 signifie que la conformité des critères communs n'est pas activée. Il s'agit du paramètre par défaut.  
  
-   1 signifie que la conformité des critères communs est activée.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant active la conformité des critères communs.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'common criteria compliance enabled', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)  
  
  

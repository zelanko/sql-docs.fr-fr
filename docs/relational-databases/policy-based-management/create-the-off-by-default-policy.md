---
title: "Cr&#233;er la strat&#233;gie D&#233;sactiv&#233; par d&#233;faut | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-query-tuning"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 98fde3c5-297c-4d95-981e-95700bbf5ccd
caps.latest.revision: 28
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Cr&#233;er la strat&#233;gie D&#233;sactiv&#233; par d&#233;faut
Cette tâche crée une condition nommée Courrier désactivé basée sur la facette Configuration de la surface d'exposition. Ensuite, elle crée une stratégie nommée Désactivé par défaut.  
  
### Pour créer la condition Courrier désactivé  
  
1.  Dans l’Explorateur d’objets, développez **Gestion**, **Gestion de la stratégie**, **Facettes**, cliquez avec le bouton droit sur **Configuration de la surface d’exposition**, puis cliquez sur **Nouvelle condition**.  
  
2.  Dans la boîte de dialogue **Créer une nouvelle condition**, dans la zone **Nom**, tapez **Mail Off**.  
  
3.  Dans la zone **Facette**, vérifiez que la facette **Configuration de la surface d’exposition** est sélectionnée.  
  
4.  Dans la zone **Expression**, dans la zone **Champ**, sélectionnez **@DatabaseMailEnabled** ; ensuite, dans la zone **Opérateur**, sélectionnez **=** ; enfin, dans **Valeur**, sélectionnez **Faux**.  
  
5.  Dans la page **Description**, entrez une description de la condition, puis cliquez sur **OK** pour créer la condition.  
  
### Pour créer la stratégie Désactivé par défaut  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur **Configuration de la surface d’exposition**, puis cliquez sur **Nouvelle stratégie**.  
  
2.  Dans la boîte de dialogue **Créer une nouvelle stratégie**, dans la zone **Nom**, tapez **Off By Default**.  
  
3.  Laissez la case **Activé** décochée. La case à cocher **Activé** s’applique aux stratégies automatisées ; cette stratégie sera exécutée à la demande.  
  
4.  Dans la case à cocher **Vérifier la condition**, faites défiler la liste jusqu’à la zone **Configuration de la surface d’exposition**, puis sélectionnez **Mail Off** comme condition à vérifier.  
  
5.  La zone **Par rapport aux cibles** est vide car il s’agit d’une stratégie dont l’étendue est le serveur.  
  
6.  Dans la case à cocher **Mode d’évaluation**, sélectionnez **À la demande**.  
  
7.  Dans la case à cocher **Restriction sur le serveur**, sélectionnez **Aucune**.  
  
8.  Dans la page **Description**, tapez une description de la stratégie.  
  
9. Vous pouvez fournir un lien hypertexte vers une page web pour vos stratégies dans la zone **Lien hypertexte d’aide supplémentaire**. Dans la zone **Texte à afficher**, tapez le texte du lien hypertexte.  
  
10. Dans la zone **Adresse**, tapez un lien hypertexte vers une page d’aide, par exemple la page d’accueil du service informatique de votre société.  
  
11. Pour vérifier l’adresse en ouvrant la page web, cliquez sur **Lien de test**.  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## Tâche suivante de la leçon  
[Configurer un serveur pour exécuter la stratégie Désactivé par défaut](../../relational-databases/policy-based-management/configure-a-server-to-run-the-off-by-default-policy.md)  
  
  
  

---
title: Démarrage de l’utilitaire en ligne de commande dta et paramétrage d’une charge de travail | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], tutorials
ms.assetid: f34a5acf-1f3b-4484-a770-6470cb925ab0
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 23534a159e659cde0b9154a5f7484f6b405f57be
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37222629"
---
# <a name="starting-the-dta-command-prompt-utility-and-tuning-a-workload"></a>Démarrage de l'utilitaire de ligne de commande dta et paramétrage d'une charge de travail
  Au cours de cette tâche, vous allez démarrer l’utilitaire **dta** et afficher son aide, puis vous allez l’utiliser afin de paramétrer une charge de travail à partir de l’invite de commandes. La charge de travail utilisée est la charge, MyScript.sql, que vous avez créée dans l’exercice sur l’interface utilisateur graphique de l’Assistant Paramétrage du moteur de base de données : [Paramétrage d’une charge de travail](lesson-1-1-tuning-a-workload.md).  
  
 Le didacticiel utilise l'exemple de base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Pour des raisons de sécurité, les exemples de bases de données ne sont pas installés par défaut. Pour installer les exemples de bases de données, consultez [Installation des exemples SQL Server et des exemples de bases de données](http://sqlserversamples.codeplex.com).  
  
 Les tâches suivantes sont destinées à vous guider pour ouvrir une invite de commandes, démarrer l’utilitaire en ligne de commande **dta** , afficher son aide sur la syntaxe et paramétrer la charge de travail simple, MyScript.sql, que vous avez créée dans le cadre de l’exercice : [Paramétrage d’une charge de travail](lesson-1-1-tuning-a-workload.md).  
  
### <a name="to-start-the-dta-command-prompt-utility-and-view-help"></a>Pour démarrer l'utilitaire de ligne de commande dta et afficher l'aide  
  
1.  Dans le menu **Démarrer** , pointez sur **Tous les programmes**, sur **Accessoires**, puis cliquez sur **Invite de commandes**.  
  
2.  À l’invite de commandes, tapez ce qui suit, puis appuyez sur Entrée :  
  
    ```  
    dta -? | more  
    ```  
  
     La section `| more` de cette commande est facultative. Sachez cependant que son utilisation permet de parcourir l'aide sur la syntaxe de l'utilitaire. Appuyez sur Entrée pour faire défiler le texte de l'aide ligne par ligne ou sur Espace pour le faire défiler page par page.  
  
### <a name="to-tune-a-simple-workload-by-using-the-dta-command-prompt-utility"></a>Pour paramétrer une charge de travail simple à l'aide de l'utilitaire de ligne de commande dta  
  
1.  À l'invite de commandes, indiquez le chemin du répertoire dans lequel vous avez stocké le fichier MyScript.sql.  
  
2.  À l'invite de commandes, tapez la commande suivante et appuyez sur Entrée pour l'exécuter et démarrer la session de paramétrage (notez que l'utilitaire respecte la distinction entre les majuscules et les minuscules lorsqu'il analyse les commandes) :  
  
    ```  
    dta -S YourServerName\YourSQLServerInstanceName -E -D AdventureWorks2012 -if MyScript.sql -s MySession2 -of MySession2OutputScript.sql -ox MySession2Output.xml -fa IDX_IV -fp NONE -fk NONE  
    ```  
  
     où `-S` spécifie le nom de votre serveur et l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans laquelle la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] est installée. Le paramètre `-E` spécifie que vous souhaitez utiliser une connexion approuvée à l'instance, ce qui est approprié si vous utilisez un compte de domaine Windows pour vous connecter. Le paramètre `-D` spécifie la base de données à paramétrer, `-if` le fichier de la charge de travail, `-s` le nom de la session, `-of` le fichier dans lequel l'outil doit enregistrer le script [!INCLUDE[tsql](../../includes/tsql-md.md)] de recommandations et enfin, le paramètre `-ox` indique le fichier dans lequel l'outil doit enregistrer les recommandations au format XML. Les trois derniers commutateurs spécifient les options de paramétrage comme suit : `-fa IDX_IV` spécifie que l'Assistant Paramétrage du moteur de base de données doit considérer uniquement l'ajout des index (cluster et non cluster) et des vues indexées ; `-fp NONE` spécifie qu'aucune stratégie de partition ne doit être prise en compte au cours de l'analyse et `-fk NONE` indique qu'aucune structure de création physique existante dans la base de données ne doit être conservée lorsque l'Assistant Paramétrage du moteur de base de données effectue ses recommandations.  
  
3.  Lorsque l'Assistant Paramétrage du moteur de base de données a terminé de paramétrer la charge de travail, il affiche un message signalant que votre session de paramétrage s'est terminée avec succès. Vous pouvez afficher les résultats du paramétrage. Pour cela, utilisez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour ouvrir les fichiers MySession2OutputScript.sql et RMySession2Output.xml. Une autre méthode consiste à ouvrir la session de paramétrage MySession2 dans l’interface de l’Assistant Paramétrage du moteur de base de données et à afficher les recommandations et les rapports en procédant comme aux exercices [Affichage des recommandations pour le paramétrage](lesson-1-2-viewing-tuning-recommendations.md) et [Affichage des rapports de paramétrage](lesson-1-3-viewing-tuning-reports.md).  
  
## <a name="summary"></a>Résumé  
 Vous avez correctement paramétré une charge de travail simple à partir de l’invite de commandes en utilisant l’utilitaire **dta** . Cet outil fournit de nombreuses autres options de paramétrage. Pour plus d’informations, consultez l’aide de cet outil (**dta -?**) et la rubrique [Utilitaire dta](dta-utility.md) .  
  
## <a name="after-you-finish-this-tutorial"></a>Fin du didacticiel  
 Une fois les leçons du didacticiel terminées, reportez-vous aux rubriques suivantes pour plus d'informations sur l'Assistant Paramétrage du moteur de base de données :  
  
-   [Assistant Paramétrage du moteur de base de données](../../relational-databases/performance/database-engine-tuning-advisor.md) : cette rubrique propose des descriptions de la façon d’effectuer des tâches avec cet outil.  
  
-   [Utilitaire dta](dta-utility.md) : cette rubrique propose des documents de référence sur l’utilitaire en ligne de commande et le fichier XML facultatif que vous pouvez utiliser pour contrôler le fonctionnement de l’utilitaire.  
  
 Pour revenir au début de ce didacticiel, consultez [Didacticiel : Assistant Paramétrage du moteur de base de données](tutorial-database-engine-tuning-advisor.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels sur le moteur de base de données](../../relational-databases/database-engine-tutorials.md)  
  
  

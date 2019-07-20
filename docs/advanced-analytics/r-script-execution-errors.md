---
title: Erreurs et résolution des problèmes liés à l’écriture de scripts R
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 83029a9727a26c647d78c49501fde08f72d7694d
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68343400"
---
# <a name="r-scripting-errors-in-sql-server"></a>Erreurs de script R dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article documente plusieurs scripts gerrors lors de l’exécution de code R dans SQL Server. La liste n’est pas exhaustive. Il existe de nombreux packages, et les erreurs peuvent varier entre les versions du même package. Nous vous recommandons de publier des erreurs de script sur le [Forum de machine learning Server](https://social.msdn.microsoft.com/Forums/en-US/home?category=MicrosoftR), qui prend en charge les composants machine learning utilisés dans R services (en base de données), Microsoft R Client et Microsoft R Server.

**S’applique à :** SQL Server 2016 R services, SQL Server 2017 Machine Learning Services


## <a name="valid-script-fails-in-t-sql-or-in-stored-procedures"></a>Échec du script valide dans T-SQL ou dans les procédures stockées

Avant d’encapsuler votre code R dans une procédure stockée, il est judicieux d’exécuter votre code R dans un environnement de développement intégré (IDE) externe ou dans l’un des outils R tels que RTerm ou RGui. À l’aide de ces méthodes, vous pouvez tester et déboguer le code en utilisant les messages d’erreur détaillés retournés par R.

Toutefois, parfois, le code qui fonctionne parfaitement dans un IDE ou un utilitaire externe peut ne pas s’exécuter dans une procédure stockée ou dans un contexte de calcul SQL Server. Dans ce cas, il existe un grand nombre de problèmes à rechercher avant que vous ne puissiez supposer que le package ne fonctionne pas dans SQL Server.

1. Vérifiez si Launchpad est en cours d’exécution.

2. Passez en revue les messages pour voir si les données d’entrée ou de sortie contiennent des colonnes avec des types de données incompatibles ou non pris en charge. Par exemple, les requêtes sur une base de données SQL retournent souvent des GUID ou des rowguid, qui ne sont pas pris en charge. Pour plus d’informations, consultez [bibliothèques et types de données R](r/r-libraries-and-data-types.md).

3. Examinez les pages d’aide des fonctions R individuelles pour déterminer si tous les paramètres sont pris en charge pour le contexte de calcul SQL Server. Pour obtenir de l’aide sur scaler, utilisez les commandes d’aide R inline ou consultez [Référence du package](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler).

Si le runtime R fonctionne mais que votre script retourne des erreurs, nous vous recommandons d’essayer de déboguer le script dans un environnement de développement R dédié, tel que Outils R pour Visual Studio.

Nous vous recommandons également de passer en revue et de réécrire légèrement le script pour corriger les problèmes liés aux types de données susceptibles de survenir lorsque vous déplacez des données entre R et le moteur de base de données. Pour plus d’informations, consultez [bibliothèques et types de données R](r/r-libraries-and-data-types.md).

En outre, vous pouvez utiliser le package sqlrutils pour regrouper votre script R dans un format qui est plus facilement utilisé comme une procédure stockée. Pour plus d'informations, consultez :
* [package sqlrutils](r/ref-r-sqlrutils.md)
* [Créer une procédure stockée à l’aide de sqlrutils](r/how-to-create-a-stored-procedure-using-sqlrutils.md)

## <a name="script-returns-inconsistent-results"></a>Le script renvoie des résultats incohérents

Les scripts R peuvent retourner des valeurs différentes dans un contexte de SQL Server, pour plusieurs raisons:

- La conversion de type implicite est effectuée automatiquement sur certains types de données, lorsque les données sont transmises entre SQL Server et R. Pour plus d’informations, consultez [bibliothèques et types de données R](r/r-libraries-and-data-types.md).

- Déterminez si le nombre de bits est un facteur. Par exemple, il existe souvent des différences dans les résultats des opérations mathématiques pour les bibliothèques à virgule flottante 32 bits et 64 bits.

- Déterminez si les valeurs NaN ont été produites dans une opération. Cela peut invalider les résultats.

- Les petites différences peuvent être amplifiées lorsque vous prenez une réciproque d’un nombre proche de zéro.

- Le cumul des erreurs d’arrondi peut entraîner des valeurs inférieures à zéro au lieu de zéro.

## <a name="implied-authentication-for-remote-execution-via-odbc"></a>Authentification implicite pour l’exécution à distance via ODBC

Si vous vous connectez à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] l’ordinateur pour exécuter des commandes R à l’aide des fonctions **RevoScaleR** , vous pouvez recevoir une erreur lorsque vous utilisez des appels ODBC qui écrivent des données sur le serveur. Cette erreur se produit uniquement lorsque vous utilisez l’authentification Windows.

Cela est dû au fait que les comptes de travail créés pour R services n’ont pas l’autorisation de se connecter au serveur. Par conséquent, les appels ODBC ne peuvent pas être exécutés à votre place. Le problème ne se produit pas avec les connexions SQL car, avec les connexions SQL, les informations d’identification sont transmises explicitement du client R à l’instance SQL Server, puis à ODBC. Toutefois, l’utilisation de connexions SQL est également moins sécurisée que l’utilisation de l’authentification Windows.

Pour permettre aux informations d’identification Windows d’être transmises en toute sécurité à partir d’un script initié à distance, SQL Server devez émuler vos informations d’identification. Ce processus est appelé _authentification implicite_. Pour que cela fonctionne, les comptes de travail qui exécutent des scripts R ou python sur l’ordinateur SQL Server doivent disposer des autorisations appropriées.

1. Ouvrez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] en tant qu’administrateur sur l’instance où vous souhaitez exécuter le code R.

2. Exécutez le script suivant. Veillez à modifier le nom du groupe d’utilisateurs, si vous avez modifié la valeur par défaut, ainsi que les noms de l’ordinateur et de l’instance.

    ```sql
    USE [master]
    GO
    
    CREATE LOGIN [computername\\SQLRUserGroup] FROM WINDOWS WITH
    DEFAULT_DATABASE=[master], DEFAULT_LANGUAGE=[language]
    GO
    ```

## <a name="avoid-clearing-the-workspace-while-youre-running-r-in-a-sql-compute-context"></a>Évitez d’effacer l’espace de travail pendant que vous exécutez R dans un contexte de calcul SQL

Bien que l’effacement de l’espace de travail soit courant lorsque vous travaillez dans la console R, il peut avoir des conséquences inattendues dans un contexte de calcul SQL.

`revoScriptConnection`est un objet dans l’espace de travail R qui contient des informations sur une session R appelée à partir de SQL Server. Toutefois, si votre code R comprend une commande permettant de supprimer l’espace de travail `rm(list=ls())`(par exemple,), toutes les informations sur la session et d’autres objets dans l’espace de travail R sont également effacées.

Pour contourner ce problème, évitez de supprimer toute discrimination des variables et d’autres objets pendant que vous exécutez R dans SQL Server. Vous pouvez supprimer des variables spécifiques à l’aide de la fonction **Remove** :

```R
remove('name1', 'name2', ...)
```

S’il existe plusieurs variables à supprimer, nous vous suggérons d’enregistrer les noms des variables temporaires dans une liste, puis d’effectuer des garbage collections périodiques dans la liste.



## <a name="next-steps"></a>Étapes suivantes

[Dépannage Machine Learning Services et problèmes connus](machine-learning-troubleshooting-faq.md)

[Collecte de données pour la résolution des problèmes Machine Learning](data-collection-ml-troubleshooting-process.md)

[FAQ sur la mise à niveau et l’installation](r/upgrade-and-installation-faq-sql-server-r-services.md)

[Résoudre les problèmes de connexion du moteur de base de données](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md)

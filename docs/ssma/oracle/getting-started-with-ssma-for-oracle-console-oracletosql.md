---
title: Bien démarrer avec SSMA pour Oracle Console (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Oracle Console, Console Output Conventions
- Oracle Console, Launching Console
ms.assetid: 667a5e4a-6848-4973-a72d-1287f64718ac
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 25cd6eb9c811548e6300c944c65c5530185d46e8
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68264504"
---
# <a name="getting-started-with-ssma--for-oracle-console-oracletosql"></a>Bien démarrer avec la console SSMA pour Oracle (OracleToSQL)
Cette section décrit la procédure pour lancer et de vous familiariser avec l’application de console Oracle. Dans la liste, dans le présent document, sont les conventions utilisées dans une fenêtre de sortie de Console SSMA classique.  
  
## <a name="launching-ssma-console"></a>Lancement de la Console SSMA  
Utilisez les étapes suivantes pour démarrer l’application de console SSMA :  
  
1.  Accédez à **Démarrer** et pointez sur **tous les programmes**.  
  
2.  Cliquez sur le  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant Migration de l’invite de commandes Oracle** raccourci.  
  
    Il affiche le menu de l’utilisation de la Console SSMA et `(/? Help)`, pour vous aider à vous familiariser avec l’application de console.  
  
## <a name="procedure-for-using-the-ssma-console"></a>Procédure d’utilisation de la Console SSMA  
Une fois que la console est lancée avec succès sur votre système Windows, vous pouvez utiliser les étapes suivantes pour travailler dessus :  
  
1.  Configurer la Console SSMA via les fichiers de script. Pour plus d’informations sur cette section, consultez [création de fichiers de Script &#40;OracleToSQL&#41; ](../../ssma/oracle/creating-script-files-oracletosql.md) .  
  
2.  [Création de fichiers de la valeur de la Variable &#40;OracleToSQL&#41;](../../ssma/oracle/creating-variable-value-files-oracletosql.md)  
  
3.  [Création des fichiers de connexion de serveur &#40;OracleToSQL&#41;](../../ssma/oracle/creating-the-server-connection-files-oracletosql.md)  
  
4.  [Exécution de la Console SSMA &#40;OracleToSQL&#41; ](../../ssma/oracle/executing-the-ssma-console-oracletosql.md) selon les besoins de votre projet  
  
Fonctionnalités supplémentaires :  
  
1.  [Spécifiez un mot de passe](managing-passwords-oracletosql.md) et exporter / importer sur d’autres ordinateurs de la fenêtre  
  
2.  [Générer des rapports](generating-reports-oracletosql.md) pour afficher le code xml détaillé des rapports pour évaluation /conversion et migration des données de sortie. Rapports d’erreurs détaillées peuvent également être générées pour les commandes Actualiser et la synchronisation.  
  
## <a name="ssma-console-output-conventions"></a>Conventions de sortie de Console SSMA  
Lors de l’exécution les commandes de script SSMA et options, le programme de console affiche les résultats et les messages (information, erreur, etc.) à l’utilisateur sur la console ou le cas échéant, redirige vers un fichier de sortie xml. Chaque type de message dans la sortie est signifié par une couleur unique. Par exemple, le message texte en couleur blanche indique les commandes du fichier de script ; celui de couleur verte représente une invite pour les entrées d’utilisateur et ainsi de suite.  
  
![Output_Oracle de Console SSMA](../../ssma/db2/media/ssmaconsoleoutput_oracle.jpg "Output_Oracle de Console SSMA")  
  
Interprétation de couleur de la sortie de console dans le tableau suivant :  
  
|Color|Description|  
|---------|---------------|  
|Rouge|Erreur irrécupérable pendant l’exécution|  
|Gris|Cachet de date et l’heure, le message à l’utilisateur|  
|Blanc|Commandes de fichier de script, type de message|  
|Jaune|Warning|  
|Vert|Invite pour l’entrée utilisateur|  
|Cyan|Guide de démarrage, terminer et le résultat d’une opération|  
  
## <a name="see-also"></a>Voir aussi  
[Installation de SSMA pour Oracle](installing-ssma-for-oracle-oracletosql.md)  
  

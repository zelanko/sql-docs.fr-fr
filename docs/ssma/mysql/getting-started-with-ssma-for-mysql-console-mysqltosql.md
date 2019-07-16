---
title: Bien démarrer avec SSMA pour MySQL Console (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- MySQL Console, launching console
- MySQL Console, output conventions
ms.assetid: 218d502c-059f-4d48-9aea-61e553d74303
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 88cf4716ea02b8c5dbcbd73e9839c6bacfbed10b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68075424"
---
# <a name="getting-started-with-ssma-for-mysql-console-mysqltosql"></a>Bien démarrer avec la console SSMA pour MySQL (MySQLToSQL)
Cette section décrit la procédure pour lancer et de vous familiariser avec l’application de console MySQL. Dans la liste, dans le présent document, sont les conventions utilisées dans une fenêtre de sortie de Console SSMA classique.  
  
## <a name="launching-ssma-console"></a>Lancement de la Console SSMA  
Utilisez les étapes suivantes pour démarrer l’application de console SSMA :  
  
1.  Accédez à **Démarrer** et pointez sur **tous les programmes**.  
  
2.  Cliquez sur le **Assistant Migration SQL Server pour l’invite de commandes MySQL** raccourci.  
  
    Il affiche le menu de l’utilisation de la Console SSMA et `(/? Help)`, pour vous aider à vous familiariser avec l’application de console.  
  
## <a name="procedure-for-using-the-ssma-console"></a>Procédure d’utilisation de la Console SSMA  
Une fois que la console est lancée avec succès sur votre système Windows, vous pouvez utiliser les étapes suivantes pour travailler dessus :  
  
1.  Configurer la Console SSMA via les fichiers de script. Pour plus d’informations sur cette section, consultez [création de fichiers de Script &#40;MySQLToSQL&#41; ](../../ssma/mysql/creating-script-files-mysqltosql.md) .  
  
2.  [Création de fichiers de la valeur de la Variable &#40;MySQLToSQL&#41;](../../ssma/mysql/creating-variable-value-files-mysqltosql.md)  
  
3.  [Création des fichiers de connexion de serveur &#40;MySQLToSQL&#41;](../../ssma/mysql/creating-the-server-connection-files-mysqltosql.md)  
  
4.  [Exécution de la Console SSMA &#40;MySQLToSQL&#41; ](../../ssma/mysql/executing-the-ssma-console-mysqltosql.md) selon les besoins de votre projet  
  
Fonctionnalités supplémentaires :  
  
1.  [Sécurisation de mot de passe](managing-passwords-mysqltosql.md) et exporter / importer sur d’autres ordinateurs de la fenêtre  
  
2.  [Générer des rapports](generating-reports-mysqltosql.md) pour afficher le code xml détaillé des rapports pour évaluation /conversion et migration des données de sortie. Rapports d’erreurs détaillées peuvent également être générées pour les commandes Actualiser et la synchronisation.  
  
## <a name="ssma-console-output-conventions"></a>Conventions de sortie de Console SSMA  
Lors de l’exécution les commandes de script SSMA et options, le programme de console affiche les résultats et les messages (information, erreur, etc.) à l’utilisateur sur la console ou le cas échéant, redirige vers un fichier de sortie xml. Chaque type de message dans la sortie est signifié par une couleur unique. Par exemple, le message texte en couleur blanche indique les commandes du fichier de script ; celui de couleur verte représente une invite pour les entrées d’utilisateur et ainsi de suite.  
  
![SSMAConsoleOutput_MySQL](../../ssma/mysql/media/ssmaconsoleoutput_mysql.jpg "SSMAConsoleOutput_MySQL")  
  
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
[Installation de SSMA pour MySQL](installing-ssma-for-mysql-mysqltosql.md)  
  

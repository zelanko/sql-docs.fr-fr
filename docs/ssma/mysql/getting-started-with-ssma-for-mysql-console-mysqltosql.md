---
title: Bien démarrer avec SSMA pour MySQL Console (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- MySQL Console, launching console
- MySQL Console, output conventions
ms.assetid: 218d502c-059f-4d48-9aea-61e553d74303
caps.latest.revision: 23
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 8f33769bee5c8d6d9e134eb9dd5dcf8549d651cb
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2018
ms.locfileid: "38983081"
---
# <a name="getting-started-with-ssma-for-mysql-console-mysqltosql"></a>Bien démarrer avec SSMA pour MySQL Console (MySQLToSQL)
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
  
1.  [Sécurisation de mot de passe](http://msdn.microsoft.com/4ffbc587-ea3f-49ad-bc42-a654f672325e) et exporter / importer sur d’autres ordinateurs de la fenêtre  
  
2.  [Générer des rapports](http://msdn.microsoft.com/1c0202e8-546d-4cb3-a37f-1d2e35d53839) pour afficher le code xml détaillé des rapports pour évaluation /conversion et migration des données de sortie. Rapports d’erreurs détaillées peuvent également être générées pour les commandes Actualiser et la synchronisation.  
  
## <a name="ssma-console-output-conventions"></a>Conventions de sortie de Console SSMA  
Lors de l’exécution les commandes de script SSMA et options, le programme de console affiche les résultats et les messages (information, erreur, etc.) à l’utilisateur sur la console ou le cas échéant, redirige vers un fichier de sortie xml. Chaque type de message dans la sortie est signifié par une couleur unique. Par exemple, le message texte en couleur blanche indique les commandes du fichier de script ; celui de couleur verte représente une invite pour les entrées d’utilisateur et ainsi de suite.  
  
![SSMAConsoleOutput_MySQL](../../ssma/mysql/media/ssmaconsoleoutput_mysql.jpg "SSMAConsoleOutput_MySQL")  
  
Interprétation de couleur de la sortie de console dans le tableau suivant :  
  
|Couleur|Description|  
|---------|---------------|  
|Rouge|Erreur irrécupérable pendant l’exécution|  
|Gris|Cachet de date et l’heure, le message à l’utilisateur|  
|White|Commandes de fichier de script, type de message|  
|Jaune|Avertissement|  
|Vert|Invite pour l’entrée utilisateur|  
|Cyan|Guide de démarrage, terminer et le résultat d’une opération|  
  
## <a name="see-also"></a>Voir aussi  
[Installation de SSMA pour MySQL](http://msdn.microsoft.com/e89b45bd-59c1-4d23-8bd7-3dafc1947448)  
  

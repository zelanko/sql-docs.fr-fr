---
description: Gestion des mots de passe (MySQLToSQL)
title: Gestion des mots de passe (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 07/06/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Password management, importing or exporting encrypted password
- Password management, securing password
ms.assetid: 4ffbc587-ea3f-49ad-bc42-a654f672325e
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 50238d3cbcd65077ad724d41c907221d5d8be998
ms.sourcegitcommit: a41e1f4199785a2b8019a419a1f3dcdc15571044
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "91988525"
---
# <a name="managing-passwords-mysqltosql"></a>Gestion des mots de passe (MySQLToSQL)
Cet article porte sur la sécurisation des mots de passe de base de données et la procédure d’importation ou d’exportation entre les serveurs.
  
## <a name="securing-password"></a>Sécurisation du mot de passe  
SSMA vous permet de sécuriser le mot de passe d’une base de données.  
  
Utilisez la procédure suivante pour implémenter une connexion sécurisée :  
  
Spécifiez un mot de passe valide à l’aide de l’une des trois méthodes suivantes :  
  
1.  **Texte en clair :** Tapez le mot de passe de la base de données dans l’attribut value du nœud « Password ». Il se trouve sous le nœud définition de serveur dans la section serveur du fichier de script ou du fichier de connexion au serveur.  
  
    Les mots de passe en texte clair ne sont pas sécurisés. Par conséquent, le message d’avertissement suivant s’affiche dans la sortie de la console : *« le serveur Server &lt; -ID &gt; Password est fourni en texte clair non sécurisé, l’application console SSMA fournit une option pour protéger le mot de passe via le chiffrement. pour plus d’informations, consultez l’option-SecurePassword dans le fichier d’aide SSMA. »*  
  
    **Mots de passe chiffrés :** Le mot de passe spécifié, dans ce cas, est stocké sous forme chiffrée sur l’ordinateur local dans ProtectedStorage. SSMA.  
  
    -   **Sécurisation des mots de passe**  
  
        -   Exécutez `SSMAforMySQLConsole.exe` avec le `-securepassword` et ajoutez le commutateur sur la ligne de commande en passant la connexion au serveur ou le fichier de script contenant le nœud de mot de passe dans la section Définition du serveur.  
  
        -   À l’invite, l’utilisateur est invité à entrer le mot de passe de la base de données et à le confirmer.  
  
            Les ID de définition de serveur et les mots de passe chiffrés correspondants sont stockés dans un fichier sur l’ordinateur local.  
            
            **Exemple 1 :**
            
            1. Spécifier le mot de passe
            
            2. `C:\SSMA\SSMAforMySQLConsole.EXE -securepassword -add all -s "D:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\AssessmentReportGenerationSample.xml" -v "D:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ VariableValueFileSample.xml"`
            
            3. Entrer le mot de passe pour server_id « XXX_1 » : xxxxxxx
            
            4. Entrez de nouveau le mot de passe pour la server_id’XXX_1 ' : xxxxxxx
            
            **Exemple 2 :**
            
            1. `C:\SSMA\SSMAforMySQLConsole.EXE -securepassword -add "source_1,target_1" -c "D:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ServersConnectionFileSample.xml" - v "D:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ VariableValueFileSample.xml" -o`
            
            2. Entrer le mot de passe pour server_id « source_1 » : xxxxxxx
            
            3. Entrez de nouveau le mot de passe pour la server_id’source_1 ' : xxxxxxx
            
            4. Entrer le mot de passe pour server_id « target_1 » : xxxxxxx
            
            5. Entrez de nouveau le mot de passe pour server_id’cible _ 1 ' : xxxxxxx
            
    -   **Suppression des mots de passe chiffrés**  
  
        Exécutez `SSMAforMySQLConsole.exe` avec le `-securepassword` commutateur et `-remove` à la ligne de commande en passant les ID de serveur, pour supprimer les mots de passe chiffrés du fichier de stockage protégé présent sur l’ordinateur local.  
  
        Exemple :  

        ```console
        C:\SSMA\SSMAforMySQLConsole.EXE -securepassword -remove all
        C:\SSMA\SSMAforMySQLConsole.EXE -securepassword -remove "source_1,target_1"  
        ```
  
    -   **Liste des ID de serveur dont les mots de passe sont chiffrés**  
  
        Exécutez le `SSMAforMySQLConsole.exe` avec le `-securepassword` `-list` commutateur et sur la ligne de commande pour répertorier tous les ID de serveur dont les mots de passe ont été chiffrés.  
  
        Exemple :  
        
        ```console
        C:\SSMA\SSMAforMySQLConsole.EXE -securepassword -list  
        ```
  
    > [!NOTE]  
    > 1.  Le mot de passe en texte clair mentionné dans le script ou le fichier de connexion du serveur est prioritaire sur le mot de passe chiffré dans fichier sécurisé.  
    > 2.  Si aucun mot de passe n’existe dans la section serveur du fichier de connexion au serveur ou dans le fichier de script ou s’il n’a pas été sécurisé sur l’ordinateur local, la console vous invite à entrer le mot de passe.  
  
## <a name="exporting-or-importing-encrypted-passwords"></a>Exportation ou importation de mots de passe chiffrés  
L’application console SSMA vous permet d’exporter les mots de passe de base de données chiffrés présents dans un fichier sur l’ordinateur local vers un fichier sécurisé, et vice-versa. Cela permet de rendre les mots de passe chiffrés indépendants de l’ordinateur.

La fonctionnalité d’exportation lit l’ID de serveur et le mot de passe à partir du stockage protégé local et enregistre les informations dans un fichier chiffré. L’utilisateur est invité à entrer le mot de passe pour le fichier sécurisé. Assurez-vous que le mot de passe entré a une longueur de 8 caractères ou plus. Ce fichier sécurisé est portable sur différents ordinateurs.

La fonctionnalité d’importation lit les informations d’ID de serveur et de mot de passe à partir du fichier sécurisé. L’utilisateur est invité à entrer le mot de passe pour le fichier sécurisé et ajoute les informations au stockage protégé local.  
  
### <a name="export-example"></a>Exemple d’exportation :  

1. Exporter le mot de passe

2. Entrer le mot de passe pour protéger le fichier exporté

3. C:\SSMA\SSMAforMySQLConsole.EXE-SecurePassword-exporter tout « machine1passwords. file »

4. Entrez le mot de passe pour protéger le fichier exporté : xxxxxxxx

5. Veuillez confirmer le mot de passe : xxxxxxxx

6. C:\SSMA\SSMAforMySQLConsole.EXE-p-e» MySQLDB_1_1, Sql_1 « machine2passwords. file »

7. Entrez le mot de passe pour protéger le fichier exporté : xxxxxxxx

8. Veuillez confirmer le mot de passe : xxxxxxxx  
  
### <a name="import-example"></a>Exemple d’importation :  

1. Importer un mot de passe chiffré

2. Entrer le mot de passe pour protéger le fichier importé

3. C:\SSMA\SSMAforMySQLConsole.EXE-SecurePassword-importer tout « machine1passwords. file »

4. Entrez le mot de passe pour importer les serveurs à partir du fichier chiffré : xxxxxxxx

5. Veuillez confirmer le mot de passe : xxxxxxxx

6. C:\SSMA\SSMAforMySQLConsole.EXE-p-i « MySQLDB_1, Sql_1 «machine2passwords. file »

7. Entrez le mot de passe pour importer les serveurs à partir du fichier chiffré : xxxxxxxx

8. Veuillez confirmer le mot de passe : xxxxxxxx  
  
## <a name="see-also"></a>Voir aussi  
[Exécution de la console SSMA (MySQL)](./executing-the-ssma-console-mysqltosql.md)  

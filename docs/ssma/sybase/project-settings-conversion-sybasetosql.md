---
title: Paramètres (Conversion) (SybaseToSQL) du projet | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: eeb80fa5-f530-4f21-beee-25f5a4b8ace6
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 5ca907bb6ce3a1f8e298c5ecefa920815cf6a8be
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47712378"
---
# <a name="project-settings-conversion-sybasetosql"></a>Paramètres du projet (Conversion) (SybaseToSQL)
La page de Conversion de la **paramètres du projet** boîte de dialogue contient les paramètres qui personnalisent comment SSMA convertit la syntaxe de Sybase Adaptive Server Enterprise (ASE) à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou la syntaxe de SQL Azure.  
  
Le volet de la Conversion est disponible dans le **paramètres du projet** et **par défaut des paramètres de projet** boîtes de dialogue :  
  
-   Si vous souhaitez spécifier des paramètres pour tous les projets SSMA, sur le **outils** menu, sélectionnez **par défaut des paramètres de projet**, cliquez sur **général** en bas du volet gauche, puis cliquez sur **Conversion**.  
  
-   Pour spécifier les paramètres pour le projet actuel, sur le **outils** menu, sélectionnez **paramètres du projet**, cliquez sur **général** en bas du volet gauche, puis cliquez sur **Conversion**.  
  
## <a name="miscellaneous-options"></a>Options diverses  
**@@ERROR**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure et des ASE utilisent différents codes d’erreur.  
  
Utilisez ce paramètre pour spécifier le type de message (avertissement ou erreur) SSMA affiche dans le volet de sortie ou de la liste d’erreurs lorsqu’il rencontre une référence à **@@ERROR**  dans le code de l’ASE.  
  
-   Si vous sélectionnez **convertir et le marquer avec l’avertissement**, SSMA convertit les instructions et les marquer avec des commentaires de l’avertissement.  
  
-   Si vous sélectionnez **marque avec l’erreur**, SSMA ignore la conversion et marquer les instructions avec des commentaires de l’erreur.  
  
Lorsque vous sélectionnez un mode de conversion dans le **Mode** boîte, SSMA s’applique le paramètre suivant :  
  
**Le Mode par défaut/Optimistic :** convertir et marquer avec avertissement  
  
**Mode complet :** marque avec l’erreur  
  
**Conversion de l’opérateur LIKE**  
Spécifie s’il faut convertir comme opérandes pour correspondre au comportement de Sybase ASE. Le point est que Sybase tronque les espaces à droite dans un motif like. La solution de contournement consiste à effectuer un cast de l’expression de droite à un type de données de longueur fixe avec une précision maximale.  
  
-   Sélectionnez **conversion Simple** pour convertir les expressions sans correction.  
  
-   Pour utiliser l’instruction select comportement ASE **casté à longueur fixe.**  
  
Lorsque vous sélectionnez un mode de conversion dans la zone Mode, SSMA s’applique le paramètre suivant :  
  
**Le Mode par défaut/Optimistic**: conversion Simple  
  
**Mode plein**: effectuer un Cast à longueur fixe  
  
**CONVERSION OU UN CAST DES CHAÎNES VIDES EN TYPES NUMÉRIQUES**  
Spécifie comment gérer les chaînes vides ou vierges dans des expressions de CAST ou de CONVERT avec un type numérique en tant qu’argument de type de données. Les options suivantes sont disponibles pour ce paramètre :  
  
-   Sélectionnez **conversion Simple** pour convertir les expressions sans correction.  
  
-   Si **vide de chaîne comme zéro numérique** est sélectionnée, le paramètre de chaîne {s} est remplacé par ltrim(rtrim({s})) cas lors de la « » puis 0 else {s} EXPRESSION fin  
  
Lorsque vous sélectionnez un mode de conversion dans la zone Mode, SSMA s’applique le paramètre suivant :  
  
**Le Mode par défaut/Optimistic**: conversion Simple  
  
**Mode plein**: aucun numérique de chaîne vide  
  
**Concaténation de NULL**  
Ce paramètre spécifie comment convertir la concaténation de chaînes avec la valeur NULL. Les options suivantes peuvent être définies pour ce paramètre particulier :  
  
-   **Retour à la ligne avec la fonction ISNULL :** si cette option est définie, chaque « string_expression » dans la concaténation non constante sera encapsulé avec ISNULL(string_expression) et les valeurs NULL seront remplacées par une chaîne vide.  
  
-   **Conserver la syntaxe actuelle**  
  
Lorsque vous sélectionnez un mode de conversion dans le **Mode** boîte, SSMA s’applique le paramètre suivant :  
  
**Le Mode par défaut/Optimistic :** conserver la syntaxe actuelle  
  
**Mode complet :** encapsuler avec la fonction ISNULL  
  
**Conversion des chaînes vides**  
Ce paramètre spécifie comment convertir des chaînes vides. Les options suivantes peuvent être définies pour ce paramètre particulier :  
  
-   **Remplacez toutes les expressions de chaîne par espace**  
  
-   **Remplacez les constantes de chaîne vide par espace**  
  
-   Pour utiliser le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ comportement de SQL Azure, sélectionnez **conserver la syntaxe actuelle**.  
  
Lorsque vous sélectionnez un mode de conversion dans le **Mode** boîte, SSMA s’applique le paramètre suivant :  
  
**Le Mode par défaut/Optimistic :** conserver la syntaxe actuelle  
  
**Mode complet :** remplacer toutes les expressions de chaîne avec un espace  
  
**Conversion de chaîne binaire CONVERT et CAST**  
La conversion des valeurs binaires en chiffres permettre retourner des valeurs différentes sur différentes plateformes. Par exemple, sur x86 processeurs, CONVERT (entier, 0 x 00000100) retourne 65536 dans ASE et 256 dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. ASE retourne également des valeurs différentes en fonction de l’ordre d’octet.  
  
Utilisez ce paramètre pour contrôler comment convertir de SSMA convertit et les expressions CASE qui contiennent des valeurs binaires :  
  
-   Sélectionnez **conversion Simple** pour convertir les expressions sans avertissements ni de correction. Utilisez ce paramètre si vous savez que le serveur de l’ASE a un ordre d’octet qui ne requiert pas de modifications de la valeur binaire.  
  
-   Sélectionnez **convertir et de corriger** avoir SSMA convertir et de corriger les expressions pour une utilisation sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L’ordre d’octet dans les constantes littérales est inversé. Toutes les autres valeurs binaires (par exemple, les binaires variables et colonnes) sont marquées avec des erreurs. Utilisez cette valeur si vous savez que le serveur de l’ASE a un ordre d’octet qui nécessite des modifications à des valeurs binaires.  
  
-   Sélectionnez **convertir et le marquer avec l’avertissement** avoir SSMA convertir et corriger les expressions et marquer toutes converti expressions avec des commentaires de l’avertissement.  
  
Lorsque vous sélectionnez un mode de conversion dans le **Mode** boîte, SSMA s’applique le paramètre suivant :  
  
**Mode par défaut :** convertir et marquer avec avertissement  
  
**Mode optimiste :** conversion Simple  
  
**Mode complet :** convertir et de corriger  
  
**SQL dynamique**  
Utilisez ce paramètre pour spécifier le type de message (avertissement ou erreur) SSMA affiche dans le volet de sortie ou de la liste d’erreurs lorsqu’il rencontre le code SQL dynamique dans le code de l’ASE.  
  
-   Si vous sélectionnez **convertir et le marquer avec l’avertissement**, SSMA va convertir le code SQL dynamique et marquer les instructions avec des commentaires de l’avertissement.  
  
-   Si vous sélectionnez **marque avec l’erreur**, SSMA ignore la conversion et marquer les instructions avec des commentaires de l’erreur.  
  
Lorsque vous sélectionnez un mode de conversion dans le **Mode** boîte, SSMA s’applique le paramètre suivant :  
  
**Le Mode par défaut/Optimistic :** convertir et marquer avec avertissement  
  
**Mode complet :** marque avec l’erreur  
  
**Conversion de vérification d’égalité**  
Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure, si le paramètre ANSI_NULLS est activé, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure retourne UNKNOWN lorsque toute comparaison d’égalité contient une valeur null. Si ANSI_NULLS est désactivée, les comparaisons d’égalité qui contiennent des valeurs null retournent true lorsque la colonne comparée et expression ou deux expressions sont tous deux null. En l’égalité de valeur par défaut (ANSINULL désactivée) Sybase ASE comparaisons se comportent comme [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure avec ANSI_NULLS OFF.  
  
-   Si vous sélectionnez **conversion Simple**, SSMA convertira le code de l’ASE à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ syntaxe SQL Azure sans contrôles supplémentaires pour les valeurs null. Utilisez ce paramètre si ANSI_NULLS est désactivé dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure ou si vous souhaitez réviser les comparaisons d’égalité au cas par cas.  
  
-   Si vous sélectionnez **valeurs envisagez NULL**, SSMA ajoutera des vérifications pour les valeurs null en utilisant les clauses IS NULL et IS NOT NULL.  
  
Lorsque vous sélectionnez un mode de conversion dans le **Mode** boîte, SSMA s’applique le paramètre suivant :  
  
**Le Mode par défaut/Optimistic :** conversion Simple  
  
**Mode complet :** envisagez NULL valeurs  
  
**Chaînes de format**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure prend en charge n’est plus le *format_string* argument dans les instructions PRINT et RAISERROR. Le *format_string* variable prise en charge de placer les paramètres remplaçables directement dans la chaîne, puis en remplaçant les paramètres lors de l’exécution. Au lieu de cela, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requiert la chaîne complète en utilisant un littéral de chaîne ou une chaîne générée en utilisant une variable. Pour plus d’informations, consultez le « PRINT ([!INCLUDE[tsql](../../includes/tsql-md.md)]) « rubrique dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne.  
  
Lorsque SSMA rencontre un *format_string* argument, il peut soit créer une chaîne littérale en utilisant les variables ou créer une nouvelle variable et générer une chaîne à l’aide de cette variable.  
  
-   Pour utiliser un littéral de chaîne pour les fonctions PRINT et RAISERROR, sélectionnez **Créer nouvelle chaîne**.  
  
    Dans ce mode, si une instruction PRINT ou RAISERROR n’utilise pas les espaces réservés et les variables locales, l’instruction est inchangée. Double caractères pourcentage (%) sont modifiées à un seul caractère de pourcentage % dans les littéraux de chaîne d’impression.  
  
    Si une instruction PRINT ou RAISERROR utilise des espaces réservés et un ou plusieurs variables locales, comme dans l’exemple suivant :  
  
    ```  
    PRINT 'Total: %1!%%', @percent  
    ```  
    SSMA convertira la syntaxe suivante :  
  
    ```  
    PRINT 'Total: '+ CAST(@percent AS varchar(max)) + '%'  
    ```  
    Si *format_string* est une variable, comme dans l’instruction suivante :  
  
    ```  
    PRINT @fmt, @arg1, @arg2  
    ```  
    SSMA ne peut pas effectuer une conversion de chaîne simple et doit créer une variable :  
  
    ```  
    DECLARE @print_format_1 varchar(max)  
    SET @print_format_1  =   
        REPLACE (@fmt, '%%', '%')  
    SET @print_format_1  =   
        REPLACE (@print_format_1, '%1!',   
        CAST (@arg1 AS varchar(max)))  
    SET @print_format_1  =   
        REPLACE (@print_format_1, '%2!',   
        CAST (@arg2 AS varchar(max)))  
    PRINT @print_format_1  
    ```  
    Lorsqu’il utilise **Créer nouvelle chaîne** mode, SSMA part du principe que le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] option CONCAT_NULL_YIELDS_NULL est désactivée (OFF). Par conséquent, SSMA ne vérifie pas pour les arguments null.  
  
-   Pour générer une nouvelle variable pour chaque instruction PRINT et RAISERROR et utilisez ensuite cette variable pour la valeur de chaîne SSMA, sélectionnez **créer une nouvelle variable**.  
  
    Dans ce mode, si une instruction PRINT ou RAISERROR n’utilise pas les espaces réservés et les variables locales, SSMA remplace tous les caractères de pourcentage double (%) par des caractères de pourcentage uniques pour se conformer aux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ syntaxe de SQL Azure.  
  
    Si une instruction PRINT ou RAISERROR utilise des espaces réservés et un ou plusieurs variables locales, comme dans l’exemple suivant :  
  
    ```  
    PRINT 'Total: %1!%%', @percent  
    ```  
    SSMA convertira la syntaxe suivante :  
  
    ```  
    DECLARE @print_format_1 varchar(max)  
    SET @print_format_1 = 'Total: %1!%'  
    SET @print_format_1  =   
        REPLACE (@print_format_1, '%1!',   
        ISNULL(CAST (@percent AS VARCHAR(max)), ''))  
    PRINT @print_format_1  
    ```  
    Si *format_string* est une variable, comme dans l’instruction suivante :  
  
    ```  
    PRINT @fmt, @arg1, @arg2  
    ```  
    SSMA crée une variable comme suit, la recherche des valeurs null dans chaque argument :  
  
    ```  
    DECLARE @print_format_1 varchar(max)  
    SET @print_format_1  =   
        REPLACE (@fmt, '%%', '%')  
    SET @print_format_1  =   
        REPLACE (@print_format_1, '%1!',   
        ISNULL(CAST (@arg1 AS varchar(max)),''))  
    SET @print_format_1  =   
        REPLACE (@print_format_1, '%2!',   
        ISNULL(CAST (@arg2 AS varchar(max)),''))  
    PRINT @print_format_1  
    ```  
  
Lorsque vous sélectionnez un mode de conversion dans le **Mode** boîte, SSMA s’applique le paramètre suivant :  
  
**Le Mode par défaut/Optimistic :** Créer nouvelle chaîne  
  
**Mode complet :** créer une nouvelle variable  
  
**Insérer une valeur explicite dans une colonne timestamp**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure ne prend pas en charge l’insertion de valeurs explicites dans une colonne timestamp.  
  
-   Pour exclure des colonnes timestamp d’instructions INSERT, sélectionnez **colonne exclure**.  
  
-   Pour imprimer un message d’erreur chaque fois qu’une colonne timestamp est dans une instruction INSERT, sélectionnez **marque avec l’erreur**. Dans ce mode, les instructions INSERT ne seront pas converties et seront marquées avec des commentaires de l’erreur.  
  
Lorsque vous sélectionnez un mode de conversion dans le **Mode** boîte, SSMA s’applique le paramètre suivant :  
  
**Le Mode par défaut/Optimistic :** colonne exclure  
  
**Mode complet :** marque avec l’erreur  
  
**Les objets temporaires définis dans les procédures de Store**  
Ce paramètre spécifie si les définitions d’objets temporaires qui apparaissent dans les procédures doivent être stockées dans les métadonnées de la source lors de la conversion.  
  
-   Sélectionnez **Oui** pour stocker les métadonnées.  
  
-   Sélectionnez **non** si les objets ne doivent pas être stockés.  
  
**Le Mode par défaut/optimiste :** Oui  
  
**Mode complet :** non  
  
**Conversion de la table proxy**  
Spécifie si les tables de proxy ASE sont converties en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ tables de SQL Azure, ou sont pas convertis et le code est marqué avec des commentaires de l’erreur.  
  
-   Sélectionnez **convertir** pour convertir les tables de proxy pour les tables normales.  
  
-   Sélectionnez **marque avec l’erreur** simplement marquer le code de la table proxy avec des commentaires de l’erreur.  
  
Lorsque vous sélectionnez un mode de conversion dans le **Mode** boîte, SSMA s’applique le paramètre suivant :  
  
**Le Mode par défaut/Optimistic/Full :** marque avec l’erreur  
  
**Nombre de messages de base de RAISERROR**  
Messages de l’utilisateur ASE sont stockés dans chaque base de données. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] messages de l’utilisateur sont stockées et accessibles par le biais de manière centralisée les **sys.messages** vue de catalogue. En outre les messages de l’utilisateur ASE démarrer à 20000, mais [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] messages d’erreur commencent à 50001.  
  
Ce paramètre spécifie le numéro à ajouter au numéro de message de l’utilisateur ASE à convertir en un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] message utilisateur. Si votre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a des messages de l’utilisateur dans le **sys.messages** (affichage catalogue), vous devrez peut-être modifier ce nombre sur une valeur plus élevée. Il s’agit donc les numéros de message converti de ne pas sont en conflit avec des numéros de message existant.  
  
Notez les points suivants :  
  
-   Messages ASE dans la plage 17000-19999 proviennent de la table système sysmessages et ne sont pas converties.  
  
-   Si le numéro du message qui est référencé dans l’instruction RAISERROR est une constante, SSMA ajoute le nombre de messages de base à la constante pour déterminer le nouveau numéro de message utilisateur.  
  
-   Si le numéro du message qui est référencé est une variable ou une expression, SSMA crée une variable locale intermédiaire.  
  
-   En mode optimiste, SSMA part du principe que le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] option CONCAT_NULL_YIELDS_NULL est désactivée et ne fait aucune vérification pour les arguments null.  
  
-   En mode complet, SSMA vérifie pour les arguments null.  
  
-   RAISERROR avec soit *liste* n’est pas converti.  
  
Lorsque vous sélectionnez un mode de conversion dans le **Mode** boîte, SSMA s’applique le paramètre suivant :  
  
**Le Mode par défaut/optimiste/Full :** 30001  
  
**Objets système**  
Utilisez ce paramètre pour spécifier le type de message (avertissement ou erreur) SSMA affiche dans le volet de sortie ou de la liste d’erreurs lorsqu’il rencontre l’utilisation des objets de système d’ASE.  
  
-   Si vous sélectionnez **convertir et le marquer avec l’avertissement**, SSMA convertira les références aux objets système et marque les instructions avec des commentaires d’avertissement.  
  
-   Si vous sélectionnez **marque avec l’erreur**, SSMA ne convertira pas de références aux objets de systèmes et marque les instructions avec des commentaires de l’erreur.  
  
Lorsque vous sélectionnez un mode de conversion dans le **Mode** boîte, SSMA s’applique le paramètre suivant :  
  
**Le Mode par défaut/Optimistic :** convertir et marquer avec avertissement  
  
**Mode complet :** marque avec l’erreur  
  
**Identificateurs non résolues**  
Utilisez ce paramètre pour spécifier le type de message (avertissement ou erreur) SSMA affiche dans le volet de sortie ou de la liste d’erreurs lorsqu’il ne peut pas résoudre un identificateur.  
  
-   Si vous sélectionnez **convertir et le marquer avec l’avertissement**, SSMA tente de convertir les références aux identificateurs non résolus et marque les instructions avec des commentaires d’avertissement.  
  
-   Si vous sélectionnez **marque avec l’erreur**, SSMA ne convertira pas de références aux identificateurs non résolues et marque les instructions avec des commentaires de l’erreur.  
  
Lorsque vous sélectionnez un mode de conversion dans le **Mode** boîte, SSMA s’applique le paramètre suivant :  
  
**Le Mode par défaut/Optimistic :** convertir et marquer avec avertissement  
  
**Mode complet :** marque avec l’erreur  
  
## <a name="system-function-options"></a>Options de fonction système  
**Fonction CHARINDEX**  
Dans l’environnement ASE, CHARINDEX retourne NULL uniquement si toutes les expressions d’entrée ont la valeur NULL. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure retourne NULL si n’importe quelle expression d’entrée a la valeur NULL.  
  
-   Pour utiliser le comportement de l’ASE, sélectionnez **remplacer la fonction**. Tous les appels à la fonction CHARINDEX est remplacé par un appel à CHARINDEX_VARCHAR ou CHARINDEX_NVARCHAR fonction définie par l’utilisateur en fonction du type des paramètres passés (créé dans la base de données utilisateur sous le nom de schéma « s2ss ») pour émuler le comportement de Sybase ASE.  
  
-   Pour utiliser le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ comportement de SQL Azure, sélectionnez **conserver la syntaxe actuelle**.  
  
Lorsque vous sélectionnez un mode de conversion dans le **Mode** boîte, SSMA s’applique le paramètre suivant :  
  
**Le Mode par défaut/Optimistic :** conserver la syntaxe actuelle  
  
**Mode complet :** remplacer (fonction)  
  
**Fonction DATALENGTH**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] / SQL Azure et ASE diffèrent dans la valeur retournée par la fonction DATALENGTH lorsque la valeur est un espace unique. Dans ce cas, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure retourne 0 et ASE retourne 1.  
  
-   Pour utiliser le comportement de l’ASE, sélectionnez **remplacer la fonction**. Tous les appels à la fonction DATALENGTH sont remplacés par l’Expression CASE pour émuler le comportement de Sybase ASE.  
  
-   Pour utiliser la valeur par défaut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] / comportement de SQL Azure, sélectionnez **conserver la syntaxe actuelle**.  
  
Lorsque vous sélectionnez un mode de conversion dans le **Mode** boîte, SSMA s’applique le paramètre suivant :  
  
**Le Mode par défaut/Optimistic :** conserver la syntaxe actuelle  
  
**Mode complet :** remplacer (fonction)  
  
**INDEX_COL (fonction)**  
ASE prend en charge facultative *user_id* argument à la fonction INDEX_COL ; Toutefois, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure ne prend pas en charge cet argument. Si vous utilisez le *user_id* argument, cette fonction ne peut pas être converti en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ syntaxe de SQL Azure.  
  
-   Pour utiliser le comportement de l’ASE, sélectionnez **convertir la fonction**. Si le code contient le *user_id* argument, SSMA affichera une erreur.  
  
-   Pour afficher un message d’erreur chaque fois que INDEX_COL est rencontré, sélectionnez **marque avec l’erreur**. SSMA ne convertira pas de références à la fonction et marque l’instruction avec des commentaires de l’erreur.  
  
**Le Mode par défaut/Optimistic/Full :** marque avec l’erreur  
  
**Fonction INDEX_COLORDER**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure n’a pas d’une fonction du système INDEX_COLORDER.  
  
-   Pour utiliser le comportement de l’ASE, sélectionnez **convertir la fonction**. Tous les appels à la fonction INDEX_COLORDER est remplacé par un appel à une fonction définie par l’utilisateur avec le même nom INDEX_COLORDER (créé dans la base de données utilisateur sous le nom de schéma « s2ss »), qui émule le comportement de Sybase ASE.  
  
-   Pour imprimer un message d’erreur chaque fois que INDEX_COLORDER est rencontré, sélectionnez **marque avec l’erreur**. SSMA ne convertira pas de références à la fonction et marque l’instruction avec des commentaires de l’erreur.  
  
Lorsque vous sélectionnez un mode de conversion dans le **Mode** boîte, SSMA s’applique le paramètre suivant :  
  
**Le Mode par défaut/Optimistic/Full :** marque avec l’erreur  
  
**Les fonctions LEFT et RIGHT**  
Gauche et droite des fonctions dans Sybase se comportent différemment pour le paramètre de longueur négative.  
  
-   Pour utiliser le comportement de l’ASE, sélectionnez **fonction Replace**. Le paramètre de longueur est ensuite remplacé par Expression CASE qui retourne null pour une valeur négative.  
  
-   Pour utiliser le comportement de SQL Server, sélectionnez **conserver la syntaxe actuelle**  
  
Lorsque vous sélectionnez un mode de conversion dans le **Mode** boîte, SSMA s’applique le paramètre suivant :  
  
**Le Mode par défaut/Optimistic :** conserver la syntaxe actuelle  
  
**Mode complet :** remplacer (fonction)  
  
> [!NOTE]  
> Si le paramètre de longueur est une valeur littérale et pas une expression complexe, la valeur de longueur est toujours remplacée par la valeur null, quel que soit le paramètre de projet.  
  
**Fonction NEXT_IDENTITY**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure n’a pas d’une fonction du système NEXT_IDENTITY.  
  
-   Pour utiliser le comportement de l’ASE, sélectionnez **convertir la fonction**. Tous les appels à la fonction NEXT_IDENTITY est remplacée par l’expression (IDENT_CURRENT(parameter Value) + IDENT_INCR(parameter Value) qui émule le comportement de Sybase ASE.  
  
-   Pour imprimer un message d’erreur chaque fois que NEXT_IDENTITY est rencontré, sélectionnez **marque avec l’erreur**. SSMA ne convertira pas de références à la fonction et marque l’instruction avec des commentaires de l’erreur.  
  
Lorsque vous sélectionnez un mode de conversion dans le **Mode** boîte, SSMA s’applique le paramètre suivant :  
  
**Le Mode par défaut/Optimistic/Full :** marque avec l’erreur  
  
**Fonction PATINDEX**  
Spécifie s’il faut convertir la fonction PATINDEX pour correspondre au comportement de Sybase ASE. Le point est que Sybase tronque les espaces à droite dans un modèle de recherche. La solution de contournement consiste à effectuer un cast de l’expression de valeur à une longueur fixe de type avec une précision maximale de données et appliquent la fonction rtrim pour rechercher le modèle.  
  
-   Pour utiliser l’instruction select comportement ASE **utiliser**.  
  
-   Pour utiliser la valeur par défaut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ comportement de SQL Azure, sélectionnez **n’utilisez pas**.  
  
Lorsque vous sélectionnez un mode de conversion dans le **Mode** boîte, SSMA s’applique le paramètre suivant :  
  
**Le Mode par défaut/Optimistic :** n’utilisez pas  
  
**Mode complet :** utilisation  
  
**REPLICATE (fonction)**  
La fonction REPLICATE répète une chaîne le nombre de fois spécifié. Dans l’environnement ASE, si vous spécifiez pour répéter la chaîne de zéro fois, le résultat est null. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure, le résultat est une chaîne vide.  
  
-   Pour utiliser le comportement de l’ASE, sélectionnez **remplacer la fonction**. Tous les appels à la fonction REPLICATE est remplacé par un appel à REPLICATE_VARCHAR ou REPLICATE_NVARCHAR fonction définie par l’utilisateur en fonction du type des paramètres passés (créé dans la base de données utilisateur sous le nom de schéma « s2ss ») pour émuler le comportement de Sybase ASE.  
  
-   Pour utiliser la valeur par défaut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ comportement de SQL Azure, sélectionnez **fonction Replace**.  
  
Lorsque vous sélectionnez un mode de conversion dans le **Mode** boîte, SSMA s’applique le paramètre suivant :  
  
**Le Mode par défaut/Optimistic Mode/Full :** remplacer (fonction)  
  
**TRIM (LTRIM, RTRIM) (fonction)**  
Ce paramètre spécifie s’il faut remplacer les appels aux fonctions de Trim (LTRIM, RTRIM) avec la syntaxe de fonctions équivalentes Sybase ASE ou conserver la syntaxe actuelle. Les options suivantes sont présentes pour ce paramètre particulier :  
  
-   **Remplacez la fonction**  
  
-   **Conserver la syntaxe actuelle**  
  
Lorsque vous sélectionnez un mode de conversion dans le **Mode** boîte, SSMA s’applique le paramètre suivant :  
  
**Le Mode par défaut/Optimistic Mode/Full :** remplacer (fonction)  
  
**SUBSTRING (fonction)**  
Dans l’environnement ASE, la fonction `SUBSTRING(expression, start, length)` retourne la valeur NULL si une valeur de début supérieure au nombre de caractères dans l’expression n’est spécifiée, ou si la longueur est égale à zéro. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure, l’expression équivalente retourne une chaîne vide.  
  
-   Pour utiliser le comportement de l’ASE, sélectionnez **remplacer la fonction**. Tous les appels à la fonction SUBSTRING est remplacé par un appel à SUBSTRING_VARCHAR ou SUBSTRING_NVARCHAR ou SUBSTRING_VARBINARY fonction définie par l’utilisateur en fonction du type des paramètres passés (créé dans la base de données utilisateur sous le nom de schéma « s2ss ») pour émuler le Comportement de Sybase ASE.  
  
-   Pour utiliser le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] / comportement de SQL Azure, sélectionnez **conserver la syntaxe actuelle**.  
  
Lorsque vous sélectionnez un mode de conversion dans le **Mode** boîte, SSMA s’applique le paramètre suivant :  
  
**Le Mode par défaut/Optimistic :** conserver la syntaxe actuelle  
  
**Mode complet :** remplacer (fonction)  
  
## <a name="tables"></a>TABLES  
**Ajouter une clé primaire**  
Crée une nouvelle clé primaire dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou une table SQL Azure si une table Access n’a aucune clé primaire ou un index unique.  
  
-   **Par défaut en Mode**: False  
  
-   **Mode optimiste**: False  
  
-   **Mode plein**: True  
  
> [!NOTE]  
> Lorsque connecté à SQL Azure, il est par défaut la valeur True.  
  
## <a name="see-also"></a>Voir aussi  
[Référence de l’Interface utilisateur &#40;SybaseToSQL&#41;](../../ssma/sybase/user-interface-reference-sybasetosql.md)  
  

---
title: Paramètres du projet (conversion) (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: eeb80fa5-f530-4f21-beee-25f5a4b8ace6
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 5d4936638fc9e283caafffc2f2a7cfdbed396920
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68028765"
---
# <a name="project-settings-conversion-sybasetosql"></a>Paramètres du projet (Conversion) (SybaseToSQL)
La page conversion de la boîte de dialogue **paramètres du projet** contient des paramètres qui personnalisent la manière dont SSMA convertit la syntaxe Sybase [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Adaptive Server Enterprise (ASE) en ou SQL Azure syntaxe.  
  
Le volet conversion est disponible dans les boîtes de dialogue **paramètres du projet** et **paramètres du projet par défaut** :  
  
-   Si vous souhaitez spécifier des paramètres pour tous les projets SSMA, dans le menu **Outils** , sélectionnez **paramètres du projet par défaut**, cliquez sur **général** en bas du volet gauche, puis sur **conversion**.  
  
-   Pour spécifier les paramètres du projet actif, dans le menu **Outils** , sélectionnez **paramètres du projet**, cliquez sur **général** en bas du volet gauche, puis sur **conversion**.  
  
## <a name="miscellaneous-options"></a>Options diverses  
**@@ERROR**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure et ASE utilisent des codes d’erreur différents.  
  
Utilisez ce paramètre pour spécifier le type de message (avertissement ou erreur) que SSMA affiche dans le volet de sortie ou de liste d’erreurs lorsqu’il rencontre une référence à **@@ERROR ** dans le code de l’ASE.  
  
-   Si vous sélectionnez **convertir et marquer avec un avertissement**, SSMA convertit les instructions et les marque avec des commentaires d’avertissement.  
  
-   Si vous sélectionnez **marquer avec une erreur**, SSMA ignore la conversion et marque les instructions avec des commentaires d’erreur.  
  
Lorsque vous sélectionnez un mode de conversion dans la zone **mode** , SSMA applique le paramètre suivant :  
  
**Mode par défaut/optimiste :** Convertir et marquer avec un avertissement  
  
**Mode complet :** Marquer avec une erreur  
  
**Conversion d’un opérateur LIKE**  
Spécifie s’il faut convertir des opérandes de type LIKE pour qu’ils correspondent au comportement de Sybase ASE. Le point est que Sybase tronque les espaces à droite dans un modèle like. La solution de contournement consiste à convertir une expression droite en type de données de longueur fixe avec une précision maximale.  
  
-   Sélectionnez **conversion simple** pour convertir les expressions sans correction.  
  
-   Pour utiliser le comportement ASE **, sélectionnez convertir en longueur fixe.**  
  
Lorsque vous sélectionnez un mode de conversion dans la zone mode, SSMA applique le paramètre suivant :  
  
**Mode par défaut/optimiste**: conversion simple  
  
**Mode complet**: cast en longueur fixe  
  
**CONVERTIR OU CONVERTIR DES CHAÎNES VIDES EN TYPES NUMÉRIQUES**  
Spécifie comment gérer des chaînes vides ou vides dans les expressions CONVERT ou CAST avec le type numérique comme argument de type de données. Les options suivantes sont disponibles pour ce paramètre :  
  
-   Sélectionnez **conversion simple** pour convertir les expressions sans correction.  
  
-   Si l’option **chaîne vide en tant que valeur numérique zéro** est sélectionnée, le paramètre de chaîne {s} est remplacé par le cas LTRIM (RTrim ({s})) quand «» Then 0 else {s} fin de l’expression  
  
Lorsque vous sélectionnez un mode de conversion dans la zone mode, SSMA applique le paramètre suivant :  
  
**Mode par défaut/optimiste**: conversion simple  
  
**Full mode**: chaîne vide en tant que valeur numérique zéro  
  
**Concaténation de NULL**  
Ce paramètre spécifie comment convertir la concaténation de chaînes avec la valeur NULL. Les options suivantes peuvent être définies pour ce paramètre particulier :  
  
-   **Encapsuler avec la fonction IsNull :** Si cette option est définie, chaque valeur « string_expression » non constante dans la concaténation est encapsulée avec ISNULL (string_expression) et les valeurs NULL sont remplacées par une chaîne vide.  
  
-   **Conserver la syntaxe actuelle**  
  
Lorsque vous sélectionnez un mode de conversion dans la zone **mode** , SSMA applique le paramètre suivant :  
  
**Mode par défaut/optimiste :** Conserver la syntaxe actuelle  
  
**Mode complet :** Wrap avec la fonction ISNULL  
  
**Conversion de chaînes vides**  
Ce paramètre spécifie comment convertir des chaînes vides. Les options suivantes peuvent être définies pour ce paramètre particulier :  
  
-   **Remplacer toutes les expressions de chaîne par des espaces**  
  
-   **Remplacer les constantes de chaîne vides par des espaces**  
  
-   Pour utiliser le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]comportement de SQL Azure, sélectionnez **conserver la syntaxe actuelle**.  
  
Lorsque vous sélectionnez un mode de conversion dans la zone **mode** , SSMA applique le paramètre suivant :  
  
**Mode par défaut/optimiste :** Conserver la syntaxe actuelle  
  
**Mode complet :** Remplacer toutes les expressions de chaîne par des espaces  
  
**Conversion de chaînes binaires CONVERT et CAST**  
La conversion de valeurs binaires en nombres peut retourner des valeurs différentes sur différentes plateformes. Par exemple, sur les processeurs x86, CONVERT (Integer, 0x00000100) retourne 65536 dans ASE et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]256 dans. ASE retourne également des valeurs différentes en fonction de l’ordre des octets.  
  
Utilisez ce paramètre pour contrôler la manière dont SSMA convertit les expressions CONVERT et CASE qui contiennent des valeurs binaires :  
  
-   Sélectionnez **conversion simple** pour convertir les expressions sans avertissement ni correction. Utilisez ce paramètre si vous savez que le serveur ASE a un ordre d’octet qui ne nécessite pas de modification de la valeur binaire.  
  
-   Sélectionnez **convertir et corriger** pour que SSMA convertisse et corrigez les expressions à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]utiliser sur. L’ordre des octets dans les constantes littérales est inversé. Toutes les autres valeurs binaires (telles que les variables et les colonnes binaires) sont signalées par des erreurs. Utilisez cette valeur si vous savez que le serveur ASE a un ordre d’octet nécessitant des modifications des valeurs binaires.  
  
-   Sélectionnez **convertir et marquer avec avertissement** pour que SSMA convertisse et corrige les expressions, et marque toutes les expressions converties avec des commentaires d’avertissement.  
  
Lorsque vous sélectionnez un mode de conversion dans la zone **mode** , SSMA applique le paramètre suivant :  
  
**Mode par défaut :** Convertir et marquer avec un avertissement  
  
**Mode optimiste :** Conversion simple  
  
**Mode complet :** Convertir et corriger  
  
**SQL dynamique**  
Utilisez ce paramètre pour spécifier le type de message (avertissement ou erreur) que SSMA affiche dans le volet de sortie ou de Liste d’erreurs lorsqu’il rencontre du code SQL dynamique dans le code de l’ASE.  
  
-   Si vous sélectionnez **convertir et marquer avec avertissement**, SSMA convertit le SQL dynamique et marque les instructions avec des commentaires d’avertissement.  
  
-   Si vous sélectionnez **marquer avec une erreur**, SSMA ignore la conversion et marque les instructions avec des commentaires d’erreur.  
  
Lorsque vous sélectionnez un mode de conversion dans la zone **mode** , SSMA applique le paramètre suivant :  
  
**Mode par défaut/optimiste :** Convertir et marquer avec un avertissement  
  
**Mode complet :** Marquer avec une erreur  
  
**Conversion de contrôle d’égalité**  
Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure, si le paramètre ANSI_NULLS est activé, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure retourne Unknown quand une comparaison d’égalité contient une valeur null. Si ANSI_NULLS est désactivé, les comparaisons d’égalité qui contiennent des valeurs NULL retournent la valeur true lorsque la colonne et l’expression comparées ou deux expressions ont la valeur null. Par défaut (ANSINULL OFF), les comparaisons d’égalité Sybase [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ASE se comportent comme/SQL Azure avec ANSI_NULLS désactivé.  
  
-   Si vous sélectionnez la **conversion simple**, SSMA convertit le code [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ASE en syntaxe/SQL Azure sans contrôles supplémentaires pour les valeurs NULL. Utilisez ce paramètre si ANSI_NULLS est désactivée dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure ou si vous souhaitez modifier les comparaisons d’égalité au cas par cas.  
  
-   Si vous sélectionnez **prendre en compte les valeurs NULL**, SSMA ajoute des vérifications pour les valeurs NULL à l’aide des clauses is null et is not null.  
  
Lorsque vous sélectionnez un mode de conversion dans la zone **mode** , SSMA applique le paramètre suivant :  
  
**Mode par défaut/optimiste :** Conversion simple  
  
**Mode complet :** Considérer les valeurs NULL  
  
**Chaînes de format**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure ne prend plus en charge l’argument *FORMAT_STRING* dans les instructions print et RAISERROR. La variable *FORMAT_STRING* prend en charge le placement des paramètres remplaçables directement dans la chaîne, puis le remplacement des paramètres au moment de l’exécution. Au lieu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de cela, requiert la chaîne complète à l’aide d’un littéral de chaîne ou d’une chaîne générée à l’aide d’une variable. Pour plus d’informations, consultez la rubrique « [!INCLUDE[tsql](../../includes/tsql-md.md)]Print () » [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans la documentation en ligne de.  
  
Lorsque SSMA rencontre un argument *FORMAT_STRING* , il peut soit générer un littéral de chaîne à l’aide des variables, soit créer une nouvelle variable et générer une chaîne à l’aide de cette variable.  
  
-   Pour utiliser un littéral de chaîne pour les fonctions PRINT et RAISERROR, sélectionnez **créer une nouvelle chaîne**.  
  
    Dans ce mode, si une instruction PRINT ou RAISERROR n’utilise pas d’espaces réservés ni de variables locales, l’instruction est inchangée. Caractères double pour cent (%%) sont remplacées par un seul caractère de pourcentage (%) dans les littéraux de chaîne d’impression.  
  
    Si une instruction PRINT ou RAISERROR utilise des espaces réservés et une ou plusieurs variables locales, comme dans l’exemple suivant :  
  
    ```  
    PRINT 'Total: %1!%%', @percent  
    ```  
    SSMA la convertit en la syntaxe suivante :  
  
    ```  
    PRINT 'Total: '+ CAST(@percent AS varchar(max)) + '%'  
    ```  
    Si *FORMAT_STRING* est une variable, par exemple dans l’instruction suivante :  
  
    ```  
    PRINT @fmt, @arg1, @arg2  
    ```  
    SSMA ne peut pas effectuer de conversion de chaîne simple et doit créer une variable :  
  
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
    Lorsqu’il utilise l’option **créer un nouveau mode de chaîne** , SSMA [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] suppose que l’option CONCAT_NULL_YIELDS_NULL est désactivée. Par conséquent, SSMA ne vérifie pas les arguments null.  
  
-   Pour que SSMA génère une nouvelle variable pour chaque instruction PRINT et RAISERROR, puis utilise cette variable pour la valeur de chaîne, sélectionnez **Create New variable**.  
  
    Dans ce mode, si une instruction PRINT ou RAISERROR n’utilise pas d’espaces réservés ni de variables locales, SSMA remplace tous les caractères double pour cent (%%) avec des caractères à un seul pourcentage pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]respecter la syntaxe/SQL Azure.  
  
    Si une instruction PRINT ou RAISERROR utilise des espaces réservés et une ou plusieurs variables locales, comme dans l’exemple suivant :  
  
    ```  
    PRINT 'Total: %1!%%', @percent  
    ```  
    SSMA la convertit en la syntaxe suivante :  
  
    ```  
    DECLARE @print_format_1 varchar(max)  
    SET @print_format_1 = 'Total: %1!%'  
    SET @print_format_1  =   
        REPLACE (@print_format_1, '%1!',   
        ISNULL(CAST (@percent AS VARCHAR(max)), ''))  
    PRINT @print_format_1  
    ```  
    Si *FORMAT_STRING* est une variable, par exemple dans l’instruction suivante :  
  
    ```  
    PRINT @fmt, @arg1, @arg2  
    ```  
    SSMA crée une variable comme suit, en vérifiant la présence de valeurs NULL dans chaque argument :  
  
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
  
Lorsque vous sélectionnez un mode de conversion dans la zone **mode** , SSMA applique le paramètre suivant :  
  
**Mode par défaut/optimiste :** Créer une nouvelle chaîne  
  
**Mode complet :** Créer une variable  
  
**Insérer une valeur explicite dans une colonne timestamp**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure ne prend pas en charge l’insertion de valeurs explicites dans une colonne timestamp.  
  
-   Pour exclure des colonnes timestamp des instructions INSERT, sélectionnez **exclure une colonne**.  
  
-   Pour imprimer un message d’erreur chaque fois qu’une colonne timestamp se trouve dans une instruction INSERT, sélectionnez **Mark with Error**. Dans ce mode, les instructions INSERT ne sont pas converties et sont marquées avec des commentaires d’erreur.  
  
Lorsque vous sélectionnez un mode de conversion dans la zone **mode** , SSMA applique le paramètre suivant :  
  
**Mode par défaut/optimiste :** Exclure une colonne  
  
**Mode complet :** Marquer avec une erreur  
  
**Stocker des objets temporaires définis dans des procédures**  
Ce paramètre spécifie si les définitions des objets temporaires qui apparaissent dans les procédures doivent être stockées dans les métadonnées sources lors de la conversion.  
  
-   Sélectionnez **Oui** pour stocker dans les métadonnées.  
  
-   Sélectionnez **non** si les objets n’ont pas besoin d’être stockés.  
  
**Mode par défaut/optimiste :** Oui  
  
**Mode complet :** º  
  
**Conversion de table proxy**  
Spécifie si les tables proxy ASE sont [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]converties en tables/SQL Azure, ou si elles ne sont pas converties et que le code est marqué avec des commentaires d’erreur.  
  
-   Sélectionnez **convertir** pour convertir les tables proxy en tables normales.  
  
-   Sélectionnez **marquer avec erreur** pour marquer simplement le code de la table proxy avec des commentaires d’erreur.  
  
Lorsque vous sélectionnez un mode de conversion dans la zone **mode** , SSMA applique le paramètre suivant :  
  
**Mode par défaut/optimiste/mode complet :** Marquer avec une erreur  
  
**Numéro de message de base RAISERROR**  
Les messages utilisateur ASE sont stockés dans chaque base de données. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]les messages utilisateur sont stockés de manière centralisée et mis à disposition par le biais de l’affichage catalogue **sys. messages** . En outre, les messages utilisateur ASE commencent à 20000 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , mais les messages d’erreur commencent à 50001.  
  
Ce paramètre spécifie le nombre à ajouter au numéro de message utilisateur de l’ASE pour le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] convertir en message utilisateur. Si votre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contient des messages utilisateur dans l’affichage catalogue **sys. messages** , vous devrez peut-être modifier ce nombre en lui attribuant une valeur plus élevée. Ainsi, les numéros des messages convertis ne sont pas en conflit avec les numéros de message existants.  
  
Notez les points suivants :  
  
-   Les messages ASE dans la plage 17000-19999 proviennent de la table système sysmessages et ne sont pas convertis.  
  
-   Si le numéro de message référencé dans l’instruction RAISERROR est une constante, SSMA ajoute le numéro de message de base à la constante pour déterminer le nouveau numéro de message utilisateur.  
  
-   Si le numéro de message référencé est une variable ou une expression, SSMA crée une variable locale intermédiaire.  
  
-   En mode optimiste, SSMA suppose que l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] option CONCAT_NULL_YIELDS_NULL est désactivée et n’effectue aucune vérification des arguments null.  
  
-   En mode complet, SSMA recherche les arguments null.  
  
-   RAISERROR avec la *liste* ERRORDATA n’est pas converti.  
  
Lorsque vous sélectionnez un mode de conversion dans la zone **mode** , SSMA applique le paramètre suivant :  
  
**Mode par défaut/optimiste/mode complet :** 30001  
  
**Objets système**  
Utilisez ce paramètre pour spécifier le type de message (avertissement ou erreur) que SSMA affiche dans le volet de sortie ou de Liste d’erreurs lorsqu’il rencontre l’utilisation d’objets système ASE.  
  
-   Si vous sélectionnez **convertir et marquer avec avertissement**, SSMA convertit les références aux objets système et marque les instructions avec des commentaires d’avertissement.  
  
-   Si vous sélectionnez **marquer avec une erreur**, SSMA ne convertit pas les références aux objets système et marque les instructions avec des commentaires d’erreur.  
  
Lorsque vous sélectionnez un mode de conversion dans la zone **mode** , SSMA applique le paramètre suivant :  
  
**Mode par défaut/optimiste :** Convertir et marquer avec un avertissement  
  
**Mode complet :** Marquer avec une erreur  
  
**Identificateurs non résolus**  
Utilisez ce paramètre pour spécifier le type de message (avertissement ou erreur) que SSMA affiche dans le volet de sortie ou de Liste d’erreurs lorsqu’il ne peut pas résoudre un identificateur.  
  
-   Si vous sélectionnez **convertir et marquer avec un avertissement**, SSMA tente de convertir les références aux identificateurs non résolus et marque les instructions avec des commentaires d’avertissement.  
  
-   Si vous sélectionnez **marquer avec une erreur**, SSMA ne convertit pas les références aux identificateurs non résolus et marque les instructions avec des commentaires d’erreur.  
  
Lorsque vous sélectionnez un mode de conversion dans la zone **mode** , SSMA applique le paramètre suivant :  
  
**Mode par défaut/optimiste :** Convertir et marquer avec un avertissement  
  
**Mode complet :** Marquer avec une erreur  
  
## <a name="system-function-options"></a>Options de fonction système  
**CHARINDEX (fonction)**  
Dans ASE, CHARINDEX retourne NULL uniquement si toutes les expressions d’entrée ont la valeur NULL. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure retourne NULL si une expression d’entrée a la valeur NULL.  
  
-   Pour utiliser le comportement ASE, sélectionnez **remplacer la fonction**. Tous les appels à la fonction CHARINDEX sont remplacés par un appel à CHARINDEX_VARCHAR ou CHARINDEX_NVARCHAR fonction définie par l’utilisateur en fonction du type de paramètres transmis (créé dans la base de données utilisateur sous le 2SS’du nom de schéma) pour émuler le comportement de Sybase ASE.  
  
-   Pour utiliser le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]comportement de SQL Azure, sélectionnez **conserver la syntaxe actuelle**.  
  
Lorsque vous sélectionnez un mode de conversion dans la zone **mode** , SSMA applique le paramètre suivant :  
  
**Mode par défaut/optimiste :** Conserver la syntaxe actuelle  
  
**Mode complet :** Replace, fonction  
  
**DATALENGTH (fonction)**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure et ASE diffèrent dans la valeur retournée par la fonction DATALENGTH lorsque la valeur est un espace unique. Dans ce cas, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure retourne 0 et ASE retourne 1.  
  
-   Pour utiliser le comportement ASE, sélectionnez **remplacer la fonction**. Tous les appels à la fonction DATALENGTH sont substitués par l’expression CASE pour émuler le comportement de Sybase ASE.  
  
-   Pour utiliser le comportement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par défaut/SQL Azure, sélectionnez **conserver la syntaxe actuelle**.  
  
Lorsque vous sélectionnez un mode de conversion dans la zone **mode** , SSMA applique le paramètre suivant :  
  
**Mode par défaut/optimiste :** Conserver la syntaxe actuelle  
  
**Mode complet :** Replace, fonction  
  
**INDEX_COL (fonction)**  
ASE prend en charge un argument *user_id* facultatif pour la fonction INDEX_COL ; Toutefois, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure ne prend pas en charge cet argument. Si vous utilisez l’argument *user_id* , cette fonction ne peut pas être [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]convertie en syntaxe/SQL Azure.  
  
-   Pour utiliser le comportement ASE, sélectionnez **convertir la fonction**. Si le code contient l’argument *user_id* , SSMA affiche une erreur.  
  
-   Pour afficher un message d’erreur chaque fois que INDEX_COL est rencontré, sélectionnez **marquer avec une erreur**. SSMA ne convertit pas les références à la fonction et marque l’instruction avec des commentaires d’erreur.  
  
**Mode par défaut/optimiste/mode complet :** Marquer avec une erreur  
  
**INDEX_COLORDER fonction)**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure n’a pas de fonction système INDEX_COLORDER.  
  
-   Pour utiliser le comportement ASE, sélectionnez **convertir la fonction**. Tous les appels à INDEX_COLORDER fonction sont remplacés par un appel à une fonction définie par l’utilisateur portant le même nom INDEX_COLORDER (créé dans la base de données utilisateur sous le 2SS’du nom de schéma) qui émule le comportement de Sybase ASE.  
  
-   Pour imprimer un message d’erreur chaque fois que INDEX_COLORDER est rencontré, sélectionnez **marquer avec une erreur**. SSMA ne convertit pas les références à la fonction et marque l’instruction avec des commentaires d’erreur.  
  
Lorsque vous sélectionnez un mode de conversion dans la zone **mode** , SSMA applique le paramètre suivant :  
  
**Mode par défaut/optimiste/mode complet :** Marquer avec une erreur  
  
**Fonctions LEFT et RIGHT**  
Les fonctions Left et Right de Sybase se comportent différemment pour le paramètre de longueur négative.  
  
-   Pour utiliser le comportement ASE, sélectionnez **remplacer la fonction**. Le paramètre de longueur est ensuite remplacé par l’expression CASE qui retournerait null pour une valeur négative.  
  
-   Pour utiliser le comportement de SQL Server, sélectionnez **conserver la syntaxe actuelle**  
  
Lorsque vous sélectionnez un mode de conversion dans la zone **mode** , SSMA applique le paramètre suivant :  
  
**Mode par défaut/optimiste :** Conserver la syntaxe actuelle  
  
**Mode complet :** Replace, fonction  
  
> [!NOTE]  
> Si le paramètre de longueur est une valeur littérale et non une expression complexe, la valeur de longueur est toujours remplacée par null, quel que soit le paramètre du projet.  
  
**NEXT_IDENTITY fonction)**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure n’a pas de fonction système NEXT_IDENTITY.  
  
-   Pour utiliser le comportement ASE, sélectionnez **convertir la fonction**. Tous les appels à NEXT_IDENTITY fonction sont remplacés par l’expression (IDENT_CURRENT (valeur de paramètre) + IDENT_INCR (valeur de paramètre) qui émule le comportement de Sybase ASE.  
  
-   Pour imprimer un message d’erreur chaque fois que NEXT_IDENTITY est rencontré, sélectionnez **marquer avec une erreur**. SSMA ne convertit pas les références à la fonction et marque l’instruction avec des commentaires d’erreur.  
  
Lorsque vous sélectionnez un mode de conversion dans la zone **mode** , SSMA applique le paramètre suivant :  
  
**Mode par défaut/optimiste/mode complet :** Marquer avec une erreur  
  
**PATINDEX, fonction**  
Spécifie s’il faut convertir la fonction PATINDEX pour qu’elle corresponde au comportement de Sybase ASE. Le point est que Sybase tronque les espaces à droite dans un modèle de recherche. La solution consiste à convertir une expression de valeur en type de données de longueur fixe avec une précision maximale et appliquer la fonction RTrim au modèle de recherche.  
  
-   Pour utiliser le comportement ASE, sélectionnez **utiliser**.  
  
-   Pour utiliser le comportement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]par défaut/SQL Azure, sélectionnez **ne pas utiliser**.  
  
Lorsque vous sélectionnez un mode de conversion dans la zone **mode** , SSMA applique le paramètre suivant :  
  
**Mode par défaut/optimiste :** Ne pas utiliser  
  
**Mode complet :** Faites  
  
**REPLICATE (fonction)**  
La fonction REPLICATE répète une chaîne le nombre de fois spécifié. Dans ASE, si vous spécifiez de répéter la chaîne zéro fois, le résultat est null. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure, le résultat est une chaîne vide.  
  
-   Pour utiliser le comportement ASE, sélectionnez **remplacer la fonction**. Tous les appels à la fonction REPLICATE sont remplacés par un appel à REPLICATE_VARCHAR ou REPLICATE_NVARCHAR fonction définie par l’utilisateur en fonction du type de paramètres transmis (créé dans la base de données utilisateur sous le 2SS’du nom du schéma) pour émuler le comportement de Sybase ASE.  
  
-   Pour utiliser le comportement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]par défaut/SQL Azure, sélectionnez **remplacer la fonction**.  
  
Lorsque vous sélectionnez un mode de conversion dans la zone **mode** , SSMA applique le paramètre suivant :  
  
**Mode par défaut/optimiste/mode complet :** Replace, fonction  
  
**Fonction TRIM (LTRIM, RTRIM)**  
Ce paramètre spécifie s’il faut remplacer les appels aux fonctions Trim (LTRIM, RTRIM) avec les fonctions de syntaxe équivalentes à Sybase ASE ou conserver la syntaxe actuelle. Les options suivantes sont disponibles pour ce paramètre particulier :  
  
-   **Replace, fonction**  
  
-   **Conserver la syntaxe actuelle**  
  
Lorsque vous sélectionnez un mode de conversion dans la zone **mode** , SSMA applique le paramètre suivant :  
  
**Mode par défaut/optimiste/mode complet :** Replace, fonction  
  
**SUBSTRING (fonction)**  
Dans ASE, la fonction `SUBSTRING(expression, start, length)` retourne null si une valeur de début supérieure au nombre de caractères dans l’expression est spécifiée, ou si la longueur est égale à zéro. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure, l’expression équivalente retourne une chaîne vide.  
  
-   Pour utiliser le comportement ASE, sélectionnez **remplacer la fonction**. Tous les appels à la fonction SUBSTRING sont substitués par un appel à SUBSTRING_VARCHAR ou SUBSTRING_NVARCHAR ou SUBSTRING_VARBINARY fonction définie par l’utilisateur en fonction du type de paramètres transmis (créé dans la base de données utilisateur sous le 2SS’du nom de schéma) pour émuler le Comportement de Sybase ASE.  
  
-   Pour utiliser le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] comportement de SQL Azure, sélectionnez **conserver la syntaxe actuelle**.  
  
Lorsque vous sélectionnez un mode de conversion dans la zone **mode** , SSMA applique le paramètre suivant :  
  
**Mode par défaut/optimiste :** Conserver la syntaxe actuelle  
  
**Mode complet :** Replace, fonction  
  
## <a name="tables"></a>TABLES  
**Ajouter une clé primaire**  
Crée une nouvelle clé primaire dans la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table ou SQL Azure si une table Access n’a pas de clé primaire ou d’index unique.  
  
-   **Mode par défaut**: false  
  
-   **Mode optimiste**: false  
  
-   **Mode complet**: true  
  
> [!NOTE]  
> En cas de connexion à SQL Azure, la valeur par défaut est true.  
  
## <a name="see-also"></a>Voir aussi  
[Référence de l’interface utilisateur &#40;SybaseToSQL&#41;](../../ssma/sybase/user-interface-reference-sybasetosql.md)  
  

---
title: Éditeur de boucle foreach (Page de Collection) | Microsoft Docs
ms.custom: ''
ms.date: 08/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.foreachloopcontainer.collection.f1
ms.assetid: 95a19dde-61ca-4d9b-aa3d-131fa4264296
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cb93cd75ea407576b8b466defa48171e4d94a1ac
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53361388"
---
# <a name="foreach-loop-editor-collection-page"></a>Éditeur de boucle Foreach (page de collection)
  La page **Collection** de la boîte de dialogue **Éditeur de boucle Foreach** permet de spécifier le type d’énumérateur et de configurer ce dernier.  
  
 Pour en savoir plus sur le conteneur de boucles Foreach et sa configuration, consultez [Conteneur de boucles Foreach](control-flow/foreach-loop-container.md) et [Configurer un conteneur de boucles Foreach](../../2014/integration-services/configure-a-foreach-loop-container.md).  
  
## <a name="static-options"></a>Options statiques  
 **Énumérateur**  
 Sélectionnez le type d'énumérateur dans la liste. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|**Énumérateur ForEach File**|Permet d'énumérer les fichiers. Si cette valeur est sélectionnée, les options dynamiques s'affichent dans la section **Énumérateur Foreach File**.|  
|**Énumérateur ForEach Item**|Permet d'énumérer les valeurs issues d'un élément. Si cette valeur d'énumérateur est sélectionnée, les options dynamiques s'affichent dans la section **Énumérateur Foreach Item**.|  
|**Énumérateur ForEach ADO**|Permet d'énumérer les tables ou les lignes au sein de tables. Si cette valeur est sélectionnée, les options dynamiques s'affichent dans la section **Énumérateur Foreach ADO**.|  
|**Énumérateur Foreach ADO.NET Schema Rowset**|Permet d'énumérer un schéma. Si cette valeur est sélectionnée, les options dynamiques s'affichent dans la section **Énumérateur Foreach ADO.NET**.|  
|**Énumérateur Foreach À partir d’une variable**|Permet d'énumérer la valeur d'une variable. Si cette valeur est sélectionnée, les options dynamiques s'affichent dans la section **Énumérateur Foreach à partir d'une variable**.|  
|**Énumérateur Foreach Nodelist**|Permet d'énumérer les nœuds d'un document XML. Si cette valeur est sélectionnée, les options dynamiques s'affichent dans la section **Énumérateur Foreach NodeList**.|  
|**Énumérateur ForEach SMO**|Permet d'énumérer un objet SMO. Si cette valeur d'énumérateur est sélectionnée, les options dynamiques s'affichent dans la section **Énumérateur Foreach SMO**.|  
|**Énumérateur Foreach Azure Blob**|Énumérez les fichiers d’objets blob à l’emplacement spécifié des objets blob. Si cette valeur est sélectionnée, les options dynamiques s’affichent dans la section **Énumérateur d’objets blob Azure Foreach**.|  
|**Énumérateur Foreach ADLS File**|Énumérer les fichiers sur ADLS avec des filtres. Si cette valeur est sélectionnée, les options dynamiques s’affichent dans la section **Énumérateur Foreach ADLS File**.|
  
 **Expressions**  
 Cliquez sur **Expressions** ou développez ce groupe pour afficher la liste des expressions de propriété existantes. Cliquez sur le bouton représentant des points de suspension **(...)** pour ajouter une expression de propriété à une propriété d’énumérateur, ou modifiez et évaluez une expression de propriété existante.  
  
 **Rubriques connexes :**  [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md), [Éditeur d’Expressions de propriété](expressions/property-expressions-editor.md), [Générateur d’expressions](expressions/expression-builder.md)  
  
## <a name="enumerator-dynamic-options"></a>Options dynamiques portant sur les énumérateurs  
  
### <a name="enumerator--foreach-file-enumerator"></a>Enumerator = Foreach File Enumerator  
 Vous utilisez l'énumérateur Foreach File pour énumérer les fichiers d'un dossier. Par exemple, si la boucle Foreach inclut une tâche SQL, vous pouvez utiliser l'énumérateur Foreach File pour énumérer les fichiers qui contiennent les instructions SQL que la tâche SQL exécute. L'énumérateur peut être configuré pour inclure les sous-dossiers.  
  
 Le contenu des dossiers et des sous-dossiers que l'énumérateur Foreach File énumère peut changer pendant l'exécution de la boucle, car les processus externes ou les tâches de la boucle ajoutent, renomment ou suppriment les fichiers pendant l'exécution de la boucle. Cela signifie qu'un certain nombre de situations inattendues peuvent se produire :  
  
-   si des fichiers sont supprimés, une tâche de la boucle Foreach peut travailler sur un jeu de fichiers différent des fichiers utilisés par les tâches à venir ;  
  
-   si des fichiers sont renommés et qu'un processus externe ajoute automatiquement des fichiers pour remplacer les fichiers renommés, la boucle Foreach peut travailler deux fois sur le même contenu de fichier ;  
  
-   si des fichiers sont ajoutés, il peut être difficile de déterminer pour quels fichiers la boucle Foreach a effectué le travail.  
  
 **Dossier**  
 Permet d'indiquer le chemin du dossier racine à énumérer.  
  
 **Parcourir**  
 Permet de rechercher et de spécifier le chemin d'accès du dossier racine.  
  
 **Fichiers**  
 Permet de spécifier les fichiers à énumérer.  
  
> [!NOTE]  
>  Utilisez le caractère étoile (*) pour indiquer les fichiers à inclure à la collection. Par exemple, pour inclure des fichiers dont le nom contient « abc », utilisez le filtre suivant : \*abc\*.  
>   
>  Lorsque vous spécifiez une extension de nom de fichier, l'énumérateur retourne également des fichiers qui ont la même extension avec des caractères supplémentaires ajoutés. (Ce comportement est identique à celui de la commande **dir** dans le système d’exploitation, qui compare aussi les noms de fichiers 8.3 à des fins de compatibilité descendante.) Ce comportement de l'énumérateur peut générer des résultats inattendus. Par exemple, vous souhaitez énumérer uniquement des fichiers Excel 2003 et vous spécifiez "*.xls". Toutefois, l'énumérateur retournera également des fichiers Excel 2007 parce que ces fichiers ont l'extension ".xlsx".  
>   
>  Vous pouvez utiliser une expression pour spécifier les fichiers à inclure dans une collection. Pour cela, développez **Expressions** dans la page **Collection**, sélectionnez la propriété **FileSpec**, puis cliquez sur le bouton de sélection (...) pour ajouter l’expression de propriété. Pour plus d’informations sur la sélection dynamique de fichiers spécifiés, consultez [SSIS défini dynamiquement masque de fichier : Spécification de fichier](https://go.microsoft.com/fwlink/?LinkId=238154)  
  
 **Complet**  
 Permet de récupérer les chemins d'accès complets des noms de fichiers indiqués. Si des caractères étoile (*) sont mentionnés dans l'option Fichiers, les chemins d'accès complets retournés par la fonction sont ceux correspondant au filtre spécifié.  
  
 **Nom uniquement**  
 Permet de ne récupérer que les noms de fichiers. Si des caractères étoile sont mentionnés dans l'option Fichiers, les noms de fichiers retournés par la fonction sont ceux correspondant au filtre spécifié.  
  
 **Nom et extension**  
 Permet de retrouver le nom et l'extension des fichiers. Si des caractères étoile sont mentionnés dans l'option Fichiers, les noms et extension de fichiers retournés par la fonction sont ceux correspondant au filtre spécifié.  
  
 **Parcourir les sous-dossiers**  
 Permet d'inclure les sous-dossiers dans l'énumération.  
  
### <a name="enumerator--foreach-item-enumerator"></a>Enumerator = Foreach Item Enumerator  
 Vous utilisez l'énumérateur Foreach Item pour énumérer les éléments d'un dossier. Vous définissez les éléments de la collection en spécifiant les colonnes et les valeurs de colonne. Les colonnes d'une ligne définissent un élément. Par exemple, un élément qui spécifie les exécutables qu'une tâche Exécuter le processus lance et le répertoire de travail que la tâche utilise a deux colonnes, une qui dresse la liste des noms d'exécutables et une qui indique le répertoire de travail. Le nombre de lignes détermine le nombre de répétitions de la boucle. Si la table a 10 lignes, la boucle se répète 10 fois.  
  
 Pour mettre à jour les propriétés de la tâche Exécuter le processus, vous associez des variables à des colonnes d'élément en utilisant l'index de la colonne. La première colonne définie dans l'élément de l'énumérateur a la valeur d'index 0, la deuxième colonne 1, etc. Les valeurs de variables sont mises à jour à chaque répétition de la boucle. Les propriétés `Executable` et `WorkingDirectory` de la tâche Exécuter le processus peuvent ensuite être mises à jour par les expressions de propriété qui utilisent ces variables.  
  
 **Définissez les éléments de la collection For Each Item**  
 Permet de fournir une valeur pour chaque colonne de la table.  
  
> [!NOTE]  
>  Une nouvelle ligne est automatiquement ajoutée à la table dès que vous saisissez des valeurs dans les colonnes composant les lignes.  
  
> [!NOTE]  
>  Si une valeur indiquée n'est pas compatible avec le type de données de la colonne dans laquelle vous insérez la valeur, le texte s'affiche alors en rouge.  
  
 **Type de données de la colonne**  
 Permet d'afficher le type de données de la colonne active.  
  
 **Supprimer**  
 Sélectionnez un élément, puis cliquez sur **Supprimer** pour le supprimer de la liste.  
  
 **Colonnes**  
 Cliquez pour configurer le type de données des colonnes constituant l'élément.  
  
 **Rubriques connexes :** [Informations de référence sur l’interface utilisateur de la boîte de dialogue Colonnes For Each Item](../../2014/integration-services/for-each-item-columns-dialog-box-ui-reference.md)  
  
### <a name="enumerator--foreach-ado-enumerator"></a>Enumerator = Foreach ADO Enumerator  
 Vous utilisez l'énumérateur ADO Foreach pour énumérer les lignes ou les tables d'un objet ADO ou ADO.NET qui est stocké dans une variable. Par exemple, si la boucle Foreach inclut une tâche de script qui écrit un dataset dans une variable, vous pouvez utiliser l'énumérateur ADO Foreach pour énumérer les lignes du dataset. Si la variable contient un dataset ADO.NET, l'énumérateur peut être configuré pour énumérer les lignes de plusieurs tables ou pour énumérer des tables.  
  
 **Variable source de l’objet ADO**  
 Sélectionnez une variable définie par l’utilisateur dans la liste ou cliquez sur \<**Nouvelle variable...**> pour en créer une.  
  
> [!NOTE]  
>  La variable doit être de type Objet ; dans le cas contraire, une erreur se produit.  
  
 **Rubriques connexes :** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [ajouter une Variable](../../2014/integration-services/add-variable.md)  
  
 **Lignes dans la première table**  
 Permet de n'énumérer que les lignes de la première table.  
  
 **Lignes dans toutes les tables (dataset ADO.NET uniquement)**  
 Permet d'énumérer les lignes de toutes les tables. Cette option n'est disponible que si les objets à énumérer sont tous des membres du même dataset ADO.NET.  
  
 **Toutes les tables (dataset ADO.NET uniquement)**  
 Permet de n'énumérer que les tables.  
  
### <a name="enumerator--foreach-adonet-schema-rowset-enumerator"></a>Enumerator = Foreach ADO.NET Schema Rowset Enumerator  
 Vous utilisez l'énumérateur d'ensemble de lignes du schéma ADO.NET Foreach pour énumérer un schéma pour une source de données spécifiée. Par exemple, si la boucle Foreach inclut une tâche d'exécution SQL, vous pouvez utiliser l'énumérateur d'ensemble de lignes du schéma ADO.NET Foreach pour énumérer des schémas tels que les colonnes de la base de données **AdventureWorks** , et la tâche d'exécution SQL pour obtenir les autorisations de schéma.  
  
 **Connexion**  
 Sélectionnez un gestionnaire de connexions ADO.NET dans la liste ou cliquez sur \<**Nouvelle connexion...**> pour en créer un.  
  
> [!IMPORTANT]  
>  Le gestionnaire de connexions ADO.NET doit utiliser un fournisseur .NET pour OLE DB. Lors de la connexion à SQL Server, il est recommandé d'utiliser le fournisseur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client, répertorié dans la section **Fournisseurs .Net pour OleDb** de la boîte de dialogue **Gestionnaire de connexions** .  
  
 **Rubriques connexes :** [Gestionnaire de connexions ADO](connection-manager/ado-connection-manager.md), [Configure ADO.NET Connection Manager](configure-ado-net-connection-manager.md)  
  
 **Schéma**  
 Permet d'indiquer le schéma à énumérer.  
  
 **Définir les restrictions**  
 Permet de définir les restrictions s'appliquant au schéma indiqué.  
  
 **Rubriques connexes :** [Restrictions de schéma, boîte de dialogue](../../2014/integration-services/schema-restrictions-dialog-box.md)  
  
### <a name="enumerator--foreach-from-variable-enumerator"></a>Enumerator = Foreach From Variable Enumerator  
 L'énumérateur Foreach à partir d'une variable permet d'énumérer les objets énumérables contenus dans la variable spécifiée. Par exemple, si la boucle Foreach inclut une tâche d'exécution SQL qui exécute une requête et enregistre le résultat dans une variable, vous pouvez utiliser l'énumérateur Foreach à partir d'une variable pour énumérer les résultats de la requête.  
  
 **Variable**  
 Sélectionnez une variable dans la liste ou cliquez sur \<**Nouvelle variable...**> pour en créer une.  
  
 **Rubriques connexes :** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [ajouter une Variable](../../2014/integration-services/add-variable.md)  
  
### <a name="enumerator--foreach-nodelist-enumerator"></a>Enumerator = Foreach NodeList Enumerator  
 L'énumérateur Foreach Nodelist permet d'énumérer un ensemble de nœuds XML qui résulte de l'application d'une expression XPath à un fichier XML. Par exemple, si la boucle Foreach inclut une tâche de script, vous pouvez utiliser l'énumérateur Foreach NodeList pour transmettre une valeur qui correspond aux critères de l'expression XPath du fichier XML à la tâche de script.  
  
 L’expression XPath qui s’applique au fichier XML est l’opération XPath externe, stockée dans la propriété OuterXPathString. Si le type d’énumération XPath a la valeur `ElementCollection`, l’énumérateur Foreach NodeList peut appliquer une expression XPath interne, stockée dans la propriété InnerXPathString, à une collection d’éléments.  
  
 Pour en savoir plus sur l'utilisation de documents et de données XML, consultez «[Employing XML in the .NET Framework](https://go.microsoft.com/fwlink/?LinkId=56214)» (en anglais) dans MSDN Library.  
  
 **DocumentSourceType**  
 Permet de sélectionner le type de source correspondant au document XML. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|**Entrée directe**|Permet de définir la source sur un document XML.|  
|**Connexion de fichiers**|Permet de sélectionner un fichier contenant le document XML.|  
|**Variable**|Permet de définir la source sur une variable contenant le document XML.|  
  
 **DocumentSource**  
 Si **DocumentSourceType** est défini sur **Entrée directe**, indiquez le code XML ou cliquez sur le bouton représentant des points de suspension (...) pour fournir le code XML nécessaire via la boîte de dialogue **Éditeur de source de document**.  
  
 Si **DocumentSourceType** est défini sur **Connexion de fichiers**, sélectionnez un gestionnaire de connexions de fichiers ou cliquez sur \<**Nouvelle connexion...**> pour en créer un.  
  
 **Rubriques connexes :** [Gestionnaire de connexions file](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Si **DocumentSourceType** est défini sur **Variable**, sélectionnez une variable existante ou cliquez sur \<**Nouvelle variable...**> pour en créer une.  
  
 **Rubriques connexes :** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [ajouter une Variable](../../2014/integration-services/add-variable.md).  
  
 **EnumerationType**  
 Permet de sélectionner le type d'énumérateur dans la liste. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|**Navigateur**|Permet d'énumérer par le biais d'un XPathNavigator.|  
|**Nœud**|Permet d'énumérer les nœuds retournés par une opération XPath.|  
|**NodeText**|Permet d'énumérer les nœuds texte retournés par une opération XPath.|  
|`ElementCollection`|Permet d'énumérer les nœuds des éléments retournés par une opération XPath.|  
  
 **OuterXPathStringSourceType**  
 Permet de sélectionner le type source correspondant à une chaîne XPath. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|**Entrée directe**|Permet de définir la source sur un document XML.|  
|**Connexion de fichiers**|Permet de sélectionner un fichier contenant le document XML.|  
|**Variable**|Permet de définir la source sur une variable contenant le document XML.|  
  
 `OuterXPathString`  
 Si **OuterXPathStringSourceType** est défini sur **Entrée directe**, fournissez la chaîne XPath.  
  
 Si **OuterXPathStringSourceType** est défini sur **Connexion de fichiers**, sélectionnez un gestionnaire de connexions de fichiers ou cliquez sur \<**Nouvelle connexion...**> pour en créer un.  
  
 **Rubriques connexes :** [Gestionnaire de connexions file](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Si **OuterXPathStringSourceType** est défini sur **Variable**, sélectionnez une variable existante ou cliquez sur \<**Nouvelle variable...>** pour en créer une.  
  
 **Rubriques connexes :** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [ajouter une Variable](../../2014/integration-services/add-variable.md).  
  
 **InnerElementType**  
 Si **EnumerationType** est défini sur `ElementCollection`, sélectionnez le type d’élément interne dans la liste.  
  
 **InnerXPathStringSourceType**  
 Permet de sélectionner le type source correspondant à une chaîne XPath interne. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|**Entrée directe**|Permet de définir la source sur un document XML.|  
|**Connexion de fichiers**|Permet de sélectionner un fichier contenant le document XML.|  
|**Variable**|Permet de définir la source sur une variable contenant le document XML.|  
  
 `InnerXPathString`  
 Si **InnerXPathStringSourceType** est défini sur **Entrée directe**, fournissez la chaîne XPath.  
  
 Si **InnerXPathStringSourceType** est défini sur **Connexion de fichiers**, sélectionnez un gestionnaire de connexions de fichiers ou cliquez sur \<**Nouvelle connexion...**> pour en créer un.  
  
 **Rubriques connexes :** [Gestionnaire de connexions file](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Si **InnerXPathStringSourceType** est défini sur **Variable**, sélectionnez une variable existante ou cliquez sur \<**Nouvelle variable...**> pour en créer une.  
  
 **Rubriques connexes :** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [ajouter une Variable](../../2014/integration-services/add-variable.md).  
  
### <a name="enumerator--foreach-smo-enumerator"></a>Enumerator = Foreach SMO Enumerator  
 L'énumérateur Foreach SMO permet d'énumérer des objets SQL-SMO (SQL Server Management Object). Par exemple, si la boucle Foreach inclut une tâche d'exécution SQL, vous pouvez utiliser l'énumérateur Foreach SMO pour énumérer les tables de la base de données **AdventureWorks** et exécuter des requêtes qui comptent le nombre de lignes dans chaque table.  
  
 **Connexion**  
 Sélectionnez un gestionnaire de connexions ADO.NET existant ou cliquez sur \<**Nouvelle connexion...**> pour en créer un.  
  
 Rubriques connexes : [Gestionnaire de connexions ADO.NET](connection-manager/ado-net-connection-manager.md), [Configure ADO.NET Connection Manager](configure-ado-net-connection-manager.md)  
  
 **Énumérer**  
 Permet de spécifier l'objet SMO à énumérer.  
  
 **Parcourir**  
 Permet de sélectionner l'énumération SMO.  
  
 **Rubriques connexes :** [Sélectionner l’énumération SMO, boîte de dialogue](../../2014/integration-services/select-smo-enumeration-dialog-box.md)  
  
### <a name="enumerator--foreach-azure-blob-enumerator"></a>Énumérateur = Énumérateur d’objets blob Azure Foreach  
 L’  **énumérateur d’objets blob Azure**permet à un package SSIS d’énumérer des fichiers d’objets blob à l’emplacement d’objets blob spécifié. Le nom du fichier d’objet blob énuméré peut être stocké dans une variable et utilisé dans des tâches dans le conteneur de boucle Foreach.  
  
 **Gestionnaire de connexions de stockage Azure**  
 Sélectionnez un gestionnaire de connexions Azure Storage existant ou créez-en un nouveau qui fait référence à un compte Azure Storage.  
  
 Rubriques connexes : [Gestionnaire de connexions Azure Storage](connection-manager/azure-storage-connection-manager.md).  
  
 **Nom du conteneur d’objets blob**  
 Spécifiez le nom du conteneur d’objets blob qui contient les fichiers d’objets blob à énumérer...  
  
 **Répertoire d’objets blob**  
 Spécifiez le nom du répertoire d’objets blob qui contient les fichiers d’objets blob à énumérer. Le répertoire d’objets blob est une structure hiérarchique virtuelle.  
  
 **Filtre de noms d’objets blob**  
 Spécifier un filtre de noms pour énumérer les fichiers avec un certain modèle de nom. Par ex. MaFeuille*.xls\* inclut les fichiers MaFeuille001.xls et MaFeuilleABC.xlsx.  
  
 **Filtre de plage de temps de/à des objets blob**  
 Spécifiez un filtre de plage de temps. Les fichiers modifiés après **TimeRangeFrom** et avant **TimeRangeTo** seront énumérés.  
### <a name="enumerator--foreach-adls-file-enumerator"></a>Énumérateur = énumérateur Foreach ADLS File  
Le **énumérateur ADLS File** permet à un package SSIS d’énumérer les fichiers sur ADLS avec des filtres. La barre oblique (`/`)-avec préfixe de chemin d’accès complet des fichiers énumérés peut être stocké dans une variable et utilisé dans les tâches à l’intérieur du conteneur de boucles Foreach.
  
**AzureDataLakeConnection**  
Spécifie un gestionnaire de connexions Azure Data Lake ou en crée un qui fait référence à un compte ADLS.   
  
**AzureDataLakeDirectory**  
Spécifie le répertoire ADLS à rechercher.
  
**FileNamePattern**  
Spécifie un filtre de nom de fichier. Seuls les fichiers dont le nom correspond au modèle spécifié seront énumérés. Les caractères génériques `*` et `?` sont pris en charge. 
  
**SearchRecursively**  
Spécifie si la recherche doit être récursive au sein du répertoire spécifié.  
  
## <a name="external-resources"></a>Ressources externes  
  
-   Entrée de blog, [SSIS For Each Node List Enumerator](https://go.microsoft.com/fwlink/?LinkId=220671), sur bidn.com.  
  
-   Entrée de blog, [SSIS défini dynamiquement masque de fichier : FileSpec](https://go.microsoft.com/fwlink/?LinkId=238154), sur beyondrelational.com.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de boucle foreach &#40;Page Général&#41;](general-page-of-integration-services-designers-options.md)   
 [Éditeur de boucle foreach &#40;Page mappage de variables&#41;](../../2014/integration-services/foreach-loop-editor-variable-mappings-page.md)   
 [Page Expressions](expressions/expressions-page.md)   
 [Conteneur de boucles For](control-flow/for-loop-container.md)  
  
  

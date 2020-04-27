---
title: Utilitaire de profileur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- command prompt utilities [SQL Server], profiler90 utility
- profiler90 utility
- Profiler [SQL Server Profiler], starting
- SQL Server Profiler, starting
- starting SQL Server Profiler
ms.assetid: e91c30a9-0d29-4f84-bcb8-e8fb62afadda
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 572644cf673c70000cee7de77f2bca9199f19675
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "68211093"
---
# <a name="profiler-utility"></a>Utilitaire profiler
  L’utilitaire **profiler** lance l’outil [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] . Les arguments facultatifs répertoriés ci-dessous dans cette rubrique permettent de contrôler le démarrage de l'application.  
  
> [!NOTE]  
>  L’utilitaire **profiler** n’est pas destiné à générer des scripts de trace. Pour en savoir plus, voir [SQL Server Profiler](sql-server-profiler/sql-server-profiler.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      profiler  
          [ /? ] |  
[  
{  
{ /U login_id [ /P password ] }  
| /E  
}  
{[ /S sql_server_name ] | [ /A analysis_services_server_name ] }  
[ /D database ]  
[ /T "template_name" ]  
[ /B { "trace_table_name" } ]  
{ [/F "filename" ] | [ /O "filename" ] }  
[ /L locale_ID ]  
[ /M "MM-DD-YY hh:mm:ss" ]  
[ /R ]  
[ /Z file_size ]  
]  
```  
  
## <a name="arguments"></a>Arguments  
 **/?**  
 Affiche le résumé de la syntaxe des arguments de **profiler** .  
  
 **/U** *login_id*  
 ID de connexion de l'utilisateur pour l'authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Les ID de connexion respectent la casse.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteWinAuthentication](../includes/ssnotewinauthentication-md.md)].  
  
 **/P** *mot de passe*  
 Indique un mot de passe spécifié par l'utilisateur pour l'authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 **/E**  
 Spécifie la connexion avec l'authentification Windows en utilisant les informations d'identification de l'utilisateur actuel.  
  
 **/S**  *sql_server_name*  
 Spécifie une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Profiler se connecte automatiquement au serveur spécifié en utilisant les informations d’authentification spécifiées dans les commutateurs **/U** et **/P** ou dans le commutateur **/E** . Pour vous connecter à une instance nommée de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], utilisez **/S** *sql_server_name*\\*instance_name*.  
  
 **/A**  *analysis_services_server_name*  
 Spécifie une instance d'Analysis Services. Profiler se connecte automatiquement au serveur spécifié en utilisant les informations d’authentification spécifiées dans les commutateurs **/U** et **/P** ou dans le commutateur **/E** . Pour vous connecter à une instance nommée de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , utilisez **/A** *analysis_services_server_name\instance_name*.  
  
 **/D** *base de données*  
 Spécifie le nom de la base de données à utiliser avec la connexion. Cette option sélectionne la base de données par défaut pour l'utilisateur spécifié si aucune base de données n'est spécifiée.  
  
 **/B "** *trace_table_name* **"**  
 Spécifie une table de trace à charger lors du démarrage du générateur de profils. Vous devez spécifier la base de données, l'utilisateur ou le schéma, ainsi que la table.  
  
 **/T"** *template_name* **"**  
 Spécifie le modèle qui sera chargé pour configurer la trace. Le nom du modèle doit être entre guillemets. Le nom du modèle doit être le répertoire de modèles système ou le répertoire de modèles utilisateur. Si deux modèles portant le même nom existent dans les deux répertoires, le modèle du répertoire système est chargé. Si aucun modèle n'existe sous le nom spécifié, le modèle standard est chargé. Notez que l’extension de fichier du modèle (.tdf) ne doit pas être spécifiée dans *template_name*. Par exemple :  
  
```  
/T "standard"  
```  
  
 **/F"** *nom de fichier* **"**  
 Spécifie le chemin et le nom d'un fichier de trace à charger lors du démarrage du générateur de profils. Le chemin complet et le nom de fichier doivent être entre guillemets. Cette option n’est pas utilisable avec **/O**.  
  
 **/O "** *nom de fichier*  **"**  
 Spécifie le chemin d'accès et le nom d'un fichier dans lequel les résultats de trace doivent être écrits. Le chemin complet et le nom de fichier doivent être entre guillemets. Cette option n’est pas utilisable avec **/F**.  
  
 **/L** *locale_ID*  
 Non disponible.  
  
 **/M "** *MM-DD-YY hh:mm:ss* **"**  
 Spécifie la date et l'heure auxquelles la trace doit s'arrêter. L'heure d'arrêt doit être indiquée entre guillemets. Spécifiez l'heure d'arrêt conformément aux paramètres du tableau ci-dessous :  
  
|Paramètre|Définition|  
|---------------|----------------|  
|MM|Mois à deux chiffres|  
|DD|Jour à deux chiffres|  
|YY|Année à deux chiffres|  
|hh|Heure à deux chiffres au format 24 heures|  
|MM|Minute à deux chiffres|  
|ss|Seconde à deux chiffres|  
  
> [!NOTE]  
>  Le format « MM-DD-YY hh:mm:ss » peut être utilisé uniquement si l’option **Utiliser des paramètres régionaux pour afficher les valeurs de date et d’heure** est activée dans [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]. Si cette option n'est pas activée, vous devez utiliser le format de date et heure « YYYY-MM-DD hh:mm:ss ».  
  
 **/R**  
 Permet la substitution du fichier de trace.  
  
 **/Z**  *file_size*  
 Spécifie la taille du fichier de trace, en mégaoctets (Mo). La taille par défaut est de 5 Mo. Si la substitution est activée, tous les fichiers de substitution sont limités à la valeur spécifiée dans cet argument.  
  
## <a name="remarks"></a>Notes  
 Pour démarrer une trace avec un modèle spécifique, utilisez les options **/S** et **/T** simultanément. Par exemple, pour démarrer une trace en utilisant le modèle Standard sur MyServer\MyInstance, entrez ce qui suit à l'invite de commandes :  
  
```  
profiler /S MyServer\MyInstance /T "Standard"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’utilitaire d’invite de commandes &#40;moteur de base de données&#41;](command-prompt-utility-reference-database-engine.md)  
  
  

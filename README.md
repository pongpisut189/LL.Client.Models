# LL.Client.Models
//i'm new for Blazor and i used Blazor radzen datatable for dynamic but i'm get an error following this code
//yes and i'm new for github sorry for this


@page "/Component"
@using System;
@using System.Data.SqlClient;
@using System.Data.SqlTypes;
@using LL.Client.Models;
@using Microsoft.AspNetCore.Authentication;
@using Microsoft.AspNetCore.Components.Authorization;
@using Microsoft.AspNetCore.Components.WebAssembly.Authentication;
@using System.ComponentModel.DataAnnotations
@using Microsoft.EntityFrameworkCore;
@using Radzen.Blazor
@using System.Linq.Dynamic.Core
@using Radzen;
@using Microsoft.Data.SqlClient;


<style>
	.columnleft {
  float: left;
  width: 20%;
}
.columnright {
  float: right;
  width: 80%;
}
</style>
<head> 
	<h1>Database</h1>
</head>
<body>
	<div class="row">
  <div class="columnleft">

	  <RadzenTextBox/>
		<RadzenButton Text="Search" Style="width: 100px; height: 25px"/>

  </div>
  <div class="columnright">
	 
      <RadzenText TextStyle="TextStyle.H3" TagName="TagName.H1" Class="my-4">
    DataGrid <strong>dynamic</strong> data support
</RadzenText>
<RadzenText TextStyle="TextStyle.Body1" Class="my-4">
    Sometimes your data comes from external API and you don't have a C# model for it. This demo shows how to implement such a scenario.
</RadzenText>

   <RadzenDataGrid Data="@Player" TItem="IDictionary<string, object>"
                         AllowFiltering="true" FilterMode="FilterMode.SimpleWithMenu" AllowPaging="true" AllowSorting="true">
            <Columns>
                    @foreach (var column in columns)
                    {
                        <RadzenDataGridColumn TItem="IDictionary<string, object>" Title="@column.Key" Type="column.Value"
                            Property="@GetColumnPropertyExpression(column.Key, column.Value)" >
                            <Template>
                                @context[@column.Key]
                            </Template>
                        </RadzenDataGridColumn>
                    }
        </Columns>
        </RadzenDataGrid>

  </div>
</div>
</body> 


  
@code {

    [System.ComponentModel.DataAnnotations.Schema.Table("Player")]
    public partial class Player
    {
        public int ID
        {
            get;
            set;
        }

        public string lastName
        {
            get;
            set;
        }

        public string  firstName
        {
            get;
            set;
        }
        public string username
        {
            get;
            set;
        }
        public string password
        {
            get;
            set;
        }
        public string age
        {
            get;
            set;
        }

    }

    public class RowRenderEventArgs<T> : object
    {
        
    }

}

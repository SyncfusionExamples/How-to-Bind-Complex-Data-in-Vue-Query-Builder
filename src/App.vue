<template>
  <div class="container">
    <ejs-querybuilder :rule="importRules"
      separator="." fieldMode="DropdownTree"
      :dataSource="complexData">
<!--       <e-columns>
        <e-column field="Employee" label="Employee"
          :columns="employeeColumns"></e-column>
          <e-column field="Name" label="Name" :columns="nameColumns" />
          <e-column field="Country" label="Country" 
            :columns="countryColumns" />
      </e-columns> -->
    </ejs-querybuilder>
  </div>
</template>
<script>
import { QueryBuilderComponent, ColumnsDirective, ColumnDirective }
  from "@syncfusion/ej2-vue-querybuilder";

  const complexData=[
  {
    Employee: {
      ID: 1001,
      DOB: new Date(1996, 4, 23),
      HireDate: new Date(2015, 3, 21),
      Salary: 1000,
      Age: 23,
      Title: "Mr"
    },
    Name: {
      FirstName: "Joe",
      LastName: "Peter"
    },
    Country: {
      State: {
        City: "San Diego",
        Zipcode: 22434
      },
      Region: "Pacific",
      Name: "USA"
    }
  },
  {
    Employee: {
      ID: 1002,
      DOB: new Date(1995, 2, 28),
      HireDate: new Date(2015, 5, 25),
      Salary: 1300,
      Age: 25,
      Title: "Mr"
    },
    Name: {
      FirstName: "Mark",
      LastName: "Lawrence"
    },
    Country: {
      State: {
        City: "Houston",
        Zipcode: 77001
      },
      Region: "South Central",
      Name: "USA"
    }
  },
  {
    Employee: {
      ID: 1003,
      DOB: new Date(1996, 7, 7),
      HireDate: new Date(2018, 9, 11),
      Salary: 1400,
      Age: 20,
      Title: "Mr"
    },
    Name: {
      FirstName: "David",
      LastName: "Malan"
    },
    Country: {
      State: {
        City: "Jersey City",
        Zipcode: 27097
      },
      Region: "Mid-Atlantic",
      Name: "USA"
    }
  }
  ];

export default {
  components: {
    "ejs-querybuilder": QueryBuilderComponent,
    "e-columns": ColumnsDirective,
    "e-column": ColumnDirective
  },
  data(){
    return{
      complexData,
      importRules: {
        condition: 'and',
        rules: [
          {
            label: 'ID',
            field: 'Employee.ID',
            type: 'number',
            operator: 'equal',
            value: 1001
          },
          {
            label: 'First Name',
            field: 'Name.FirstName',
            type: 'string',
            operator: 'equal',
            value: 'Mark',
          },
          {
            condition: 'or',
            rules: [
              {
                label: 'City',
                field: 'Country.State.City',
                operator: 'equal',
                type: 'string',
                value: 'Jersey City',
              },
              {
                label: 'Date of birth',
                field: 'Employee.DOB',
                operator: 'equal',
                type: 'date',
                value: '7/7/96',
              },
            ],
          }
        ]
      },
      employeeColumns:[
        { field: 'ID', label: 'ID', type: 'number' },
        { field: 'DOB', label: 'Date of birth', type: 'date' },
        { field: 'HireDate', label: 'Hire Date', type: 'date' },
        { field: 'Salary', label: 'Salary', type: 'number' },
        { field: 'Age', label: 'Age', type: 'number' },
        { field: 'Title', label: 'Title', type: 'string' }
      ],
      nameColumns: [
        { field: 'FirstName', label: 'First Name', type: 'string' },
        { field: 'LastName', label: 'Last Name', type: 'string' },
      ],
      countryColumns: [
        {
          field: 'State',
          label: 'State',
          columns: [
            { field: 'City', label: 'City', type: 'string' },
            { field: 'Zipcode', label: 'Zip Code', type: 'number' },
          ],
        },
        { field: 'Region', label: 'Region', type: 'string' },
        { field: 'Name', label: 'Country Name', type: 'string' },
      ]
    }
  }
};
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-lists/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-querybuilder/styles/material.css";

.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 95%;
  margin: 0 auto;
  position: absolute;
  top: 20px;
  left: 50%;
  transform: translateX(-50%);
}
</style>
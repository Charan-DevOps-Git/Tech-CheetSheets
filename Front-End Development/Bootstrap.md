# Introduction

Bootstrap is a powerful, open-source front-end framework for developing responsive and mobile-first websites. It includes CSS- and JavaScript-based design templates for typography, forms, buttons, navigation, and other interface components.

# Basic Setup - Include Bootstrap CSS and JS:

- Via CDN:
```
<link href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css" rel="stylesheet">
<script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.5.3/dist/umd/popper.min.js"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>
```

- Via npm:
```
npm install bootstrap
```

- Include in your project:
```
<link href="node_modules/bootstrap/dist/css/bootstrap.min.css" rel="stylesheet">
<script src="node_modules/bootstrap/dist/js/bootstrap.bundle.min.js"></script>
```

# Grid System

- Container: .container, .container-fluid
- Row: .row
- Columns: ```.col, .col-* (1-12), .col-sm-*, .col-md-*, .col-lg-*, .col-xl-*```
```
<div class="container">
    <div class="row">
        <div class="col-md-4">Column 1</div>
        <div class="col-md-4">Column 2</div>
        <div class="col-md-4">Column 3</div>
    </div>
</div>
```

# Typography

- Headings: ```<h1>-<h6>, .h1-.h6```
- Display Headings: .display-1-.display-4
- Lead: .lead
- Text alignment: .text-left, .text-center, .text-right
- Text colors: .text-primary, .text-secondary, .text-success, .text-danger, .text-warning, .text-info, .text-light, .text-dark, .text-muted, .text-white
```
<h1 class="display-1">Display 1</h1>
<p class="lead">This is a lead paragraph.</p>
<p class="text-primary">This is a primary text.</p>
```

# Buttons

- Basic buttons: .btn, .btn-primary, .btn-secondary, .btn-success, .btn-danger, .btn-warning, .btn-info, .btn-light, .btn-dark, .btn-link
- Button sizes: .btn-lg, .btn-sm
- Block buttons: .btn-block
```
<button class="btn btn-primary">Primary Button</button>
<button class="btn btn-success btn-lg">Large Success Button</button>
<button class="btn btn-danger btn-block">Block Level Danger Button</button>
```
# Forms
```
- Basic form elements: <form>, <input>, <textarea>, <select>
- Form controls: .form-control
- Form groups: .form-group
- Labels: <label>
- Form grid: .row, .col-*
- Inline forms: .form-inline
- Form validation: .was-validated, .is-valid, .is-invalid
```
```
<form>
    <div class="form-group">
        <label for="exampleInputEmail1">Email address</label>
        <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp">
    </div>
    <div class="form-group">
        <label for="exampleInputPassword1">Password</label>
        <input type="password" class="form-control" id="exampleInputPassword1">
    </div>
    <button type="submit" class="btn btn-primary">Submit</button>
</form>
```

# Components

- Alerts: .alert, .alert-primary, .alert-secondary, .alert-success, .alert-danger, .alert-warning, .alert-info, .alert-light, .alert-dark
```
<div class="alert alert-success" role="alert">
    This is a success alert—check it out!
</div>
```

- Badges: .badge, .badge-primary, .badge-secondary, .badge-success, .badge-danger, .badge-warning, .badge-info, .badge-light, .badge-dark
```
<span class="badge badge-primary">Primary</span>
```

- Cards: .card, .card-body, .card-title, .card-text, .card-img-top, .card-header, .card-footer, .card-group
```
<div class="card" style="width: 18rem;">
    <img src="..." class="card-img-top" alt="...">
    <div class="card-body">
        <h5 class="card-title">Card title</h5>
        <p class="card-text">Some quick example text.</p>
        <a href="#" class="btn btn-primary">Go somewhere</a>
    </div>
</div>
```

- Navs and Navbar: .nav, .nav-item, .nav-link, .navbar, .navbar-brand, .navbar-nav, .navbar-toggler, .navbar-collapse
```
<nav class="navbar navbar-expand-lg navbar-light bg-light">
    <a class="navbar-brand" href="#">Navbar</a>
    <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
            <li class="nav-item">
                <a class="nav-link" href="#">Home</a>
            </li>
            <li class="nav-item">
                <a class="nav-link" href="#">Features</a>
            </li>
            <li class="nav-item">
                <a class="nav-link" href="#">Pricing</a>
            </li>
        </ul>
    </div>
</nav>
```

- Modals: .modal, .modal-dialog, .modal-content, .modal-header, .modal-body, .modal-footer
```
<button type="button" class="btn btn-primary" data-toggle="modal" data-target="#exampleModal">
    Launch demo modal
</button>

<div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
    <div class="modal-dialog">
        <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title" id="exampleModalLabel">Modal title</h5>
                <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                    <span aria-hidden="true">&times;</span>
                </button>
            </div>
            <div class="modal-body">
                ...
            </div>
            <div class="modal-footer">
                <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                <button type="button" class="btn btn-primary">Save changes</button>
            </div>
        </div>
    </div>
</div>
```

- Tooltips: .tooltip, data-toggle="tooltip", title
```
<button type="button" class="btn btn-secondary" data-toggle="tooltip" data-placement="top" title="Tooltip on top">
    Tooltip on top
</button>

<script>
    $(function () {
        $('[data-toggle="tooltip"]').tooltip();
    });
</script>
```

- Collapse: .collapse, .collapse.show
```
<p>
    <a class="btn btn-primary" data-toggle="collapse" href="#collapseExample" role="button" aria-expanded="false" aria-controls="collapseExample">
        Link with href
    </a>
</p>
<div class="collapse" id="collapseExample">
    <div class="card card-body">
        Anim pariatur cliche reprehenderit, enim eiusmod high life accusamus terry richardson ad squid.
    </div>
</div>
```

# Utilities

- Spacing: .m-* (margin), .p-* (padding) where * is from 0 to 5 or auto
- Text: .text-left, .text-center, .text-right, .text-justify, .text-nowrap, .text-lowercase, .text-uppercase, .text-capitalize
- Background: .bg-primary, .bg-secondary, .bg-success, .bg-danger, .bg-warning, .bg-info, .bg-light, .bg-dark, .bg-white
- Borders: .border, .border-* (top, right, bottom, left), .border-0, .border-primary, .rounded, .rounded-* (top, right, bottom, left, circle, pill)
```
<div class="p-3 mb-2 bg-primary text-white">.bg-primary</div>
<div class="border border-success rounded">Bordered and Rounded</div>
```

# Responsive Utilities

- Display: .d-*, .d-*-* (none, inline, inline-block, block, table, table-cell, table-row, flex, inline-flex) with breakpoints (sm, md, lg, xl)
```
<div class="d-none d-md-block">
    This content will be hidden on small screens and visible on medium and larger screens.
</div>
```

# Resources
[Bootstrap Documentation](https://getbootstrap.com/docs/4.1/getting-started/introduction)

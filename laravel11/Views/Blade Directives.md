### Echoing Data
- `{{ }}` - Outputs data escaped for HTML.
- `{!! !!}` - Outputs data without escaping.
- `{-- --}` - Comments
### Other Features
- `@verbatim` - Outputs raw Blade code without parsing.
- `@lang` - Translates a string using Laravel’s localization.
- `@json` - Encodes a PHP variable to JSON and outputs it.
- `@dump` - Dumps the contents of a variable (for debugging).
### Useful Directives
- `@include` - Includes a Blade view within another view.
- `@extends` - Specifies which layout the view should extend.
- `@section` - Defines a section that a layout will yield.
- `@yield` - Outputs the content of a section.
- `@show` - Outputs the content of a section and marks it as visible.
- `@push` - Pushes content onto a stack.
- `@stack` - Displays the contents of a stack.
- `@csrf` - Outputs a CSRF token field for forms.
- `@method` - Specifies a form method (e.g., `PUT` or `DELETE`).
- `@route` - Generates a URL for a named route.
### Control Structures
- `@if` - Starts an `if` statement.
- `@elseif` - Starts an `elseif` statement.
- `@else` - Starts an `else` statement.
- `@unless` - Starts an `unless` statement (opposite of `@if`).
- `@isset` - Starts a block that runs if a variable is set and not `null`.
- `@empty` - Starts a block that runs if a variable is empty.
- `@auth` - Starts a block that runs if the user is authenticated.
- `@guest` - Starts a block that runs if the user is a guest.
- `@switch` - Starts a `switch` statement.
- `@case` - Defines a case in a `switch` statement.
- `@break` - Exits a `switch` case.
- `@continue` - Continues to the next iteration of a `foreach` loop.
### Looping
- `@for` - Starts a `for` loop.
- `@endfor` - Ends a `for` loop.
- `@foreach` - Starts a `foreach` loop.
- `@endforeach` - Ends a `foreach` loop.
- `@forelse` - Starts a `foreach` loop with an `else` condition.
- `@empty` - Used with `@forelse` to display content when the collection is empty.
- `@while` - Starts a `while` loop.
- `@endwhile` - Ends a `while` loop.
### Blade Components // legacy
- replaced by the `<x-component />`  functionality
- `@component` - Includes a Blade component.
- `@endcomponent` - Ends the Blade component.
- `@props` - Defines component properties.
- `@componentSlot` - Defines a slot for a component.


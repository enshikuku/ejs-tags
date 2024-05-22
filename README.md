### EJS Tags:

1. **<% ... %>** 
   - **Purpose:** Scriptlet tag for control-flow with no output.
   - **Usage:** Used to run JavaScript code without producing any HTML output.
   - **Example:** `<% if (user) { %>`

2. **<%_ ... _%>**
   - **Purpose:** Whitespace Slurping Scriptlet tag.
   - **Usage:** Similar to `<% ... %>` but also removes all whitespace before it.
   - **Example:** `<%_ if (user) { _%>`

3. **<%= ... %>**
   - **Purpose:** Outputs the value into the template with HTML escaping.
   - **Usage:** Used to output variables in a safe manner to prevent XSS attacks.
   - **Example:** `<%= user.name %>` (if `user.name` is `<script>`, it will be escaped to `&lt;script&gt;`)

4. **<%- ... %>**
   - **Purpose:** Outputs the unescaped value into the template.
   - **Usage:** Used to output raw HTML. Use with caution to avoid XSS vulnerabilities.
   - **Example:** `<%- user.bio %>` (outputs raw HTML, so if `user.bio` is `<b>bold</b>`, it will render as bold text)

5. **<%# ... %>**
   - **Purpose:** Comment tag with no execution and no output.
   - **Usage:** Used for adding comments in the EJS code that will not appear in the HTML output.
   - **Example:** `<%# This is a comment %>`

6. **<%% ... %%>**
   - **Purpose:** Outputs a literal '<%'.
   - **Usage:** Used when you need to include the EJS delimiter itself in the output.
   - **Example:** `<%%= user.name %>` outputs `<%= user.name %>`

7. **%>**
   - **Purpose:** Plain ending tag.
   - **Usage:** Closes an EJS tag.
   - **Example:** `<% if (user) { %> Hello, <%= user.name %> <% } %>`

8. **-%>**
   - **Purpose:** Trim-mode ('newline slurp') ending tag.
   - **Usage:** Closes an EJS tag and trims the following newline.
   - **Example:** 
     ```ejs
     <% if (user) { %>
     Hello, <%= user.name %>
     <% } -%>
     ```

9. **_%>**
   - **Purpose:** Whitespace Slurping ending tag.
   - **Usage:** Closes an EJS tag and removes all whitespace after it.
   - **Example:** 
     ```ejs
     <%_ if (user) { _%>
     Hello, <%= user.name %>
     <%_ } _%>
     ```

### Usage Examples:

- **Control Flow Example:**
  ```ejs
  <% if (user) { %>
    <p>Hello, <%= user.name %></p>
  <% } else { %>
    <p>Hello, Guest</p>
  <% } %>
  ```
  This checks if a `user` object exists. If it does, it outputs "Hello, [user's name]". Otherwise, it outputs "Hello, Guest".

- **Unescaped Output Example:**
  ```ejs
  <%- include('header.ejs') %>
  ```
  This includes a file named `header.ejs` and outputs its content directly without escaping.

- **Comment Example:**
  ```ejs
  <%# This will not be included in the output %>
  <p>Visible content</p>
  ```

By understanding these tags, you can effectively manage the flow of logic and the output in your EJS templates, ensuring that your HTML is generated correctly and securely.
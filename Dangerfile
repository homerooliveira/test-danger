# Make it more obvious that a PR is a work in progress and shouldn't be merged yet
warn("PR is classed as Work in Progress") if github.pr_title.include? "[WIP]"

warn("Big PR") if git.lines_of_code > 500

modified_files = git.modified_files + git.added_files

has_source_changes = !modified_files.grep(/Source/).empty?
has_test_changes = !modified_files.grep(/Tests/).empty?

if git.lines_of_code > 50 && has_source_changes && !has_test_changes
    warn 'This PR may need tests.'
end
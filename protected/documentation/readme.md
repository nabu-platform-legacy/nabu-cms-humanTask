create sequence seq_human_tasks;

create table human_tasks (
	id uuid references nodes(id) primary key,
	created timestamp not null,
	modified timestamp not null,
	correlation_id text,
	group_id text,
	context_id text,
	human_task_type_id uuid references master_data_entries(id) not null,
	state_id uuid references master_data_entries(id) not null,
	assigned_to_id uuid references users(id),
	task_index bigint not null default nextval('seq_human_tasks'),
);